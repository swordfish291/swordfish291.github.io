# Getting Started with Azure Bicep: An Introduction

Hello everyone! As more organizations shift towards cloud-native solutions, the importance of managing and deploying resources effectively has never been greater. This is where the concept of Infrastructure as Code (IaC) comes into play. Today, I'd like to introduce you to Microsoft's answer to IaC for Azure: Azure Bicep.

Infrastructure as Code (IaC) has revolutionized the way we think about provisioning and maintaining cloud resources. For quite some time, Azure Resource Manager (ARM) templates have been the standard for defining and deploying infrastructure in Azure. They served well, but as users started building more complex environments, several pain points emerged:

Verbosity: ARM templates, being JSON-based, often resulted in long, repetitive configurations, making them hard to write and maintain.

Readability: The structure of ARM templates, while powerful, could be hard to interpret, especially for those new to the Azure platform.

Learning Curve: Writing and debugging ARM templates required a steep learning curve, slowing down the onboarding process for newcomers.

Modularity: As infrastructure grew in complexity, reusing and organizing code became increasingly important, a need that ARM templates couldn't address as efficiently.

Recognizing these challenges, Microsoft developed Azure Bicep. Bicep aims to provide a more concise, readable, and intuitive domain-specific language (DSL) for defining infrastructure on Azure. It is not just a replacement, but an evolution, ensuring a better developer experience while maintaining the power and flexibility that ARM templates offered.

Azure Bicep is designed with a clear focus on simplifying the IaC process, making Azure deployments more approachable, while still harnessing the capabilities of ARM underneath.

To better understand the shift from ARM templates to Bicep, let's look at how each would define a simp

### 1. ARM Template (JSON)
```
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "apiVersion": "2021-04-01",
      "name": "mystorageaccount",
      "location": "[resourceGroup().location]",
      "sku": {
        "name": "Standard_LRS"
      },
      "kind": "StorageV2",
      "properties": {}
    }
  ]
}
```

### 2. Azure Bicep
```
resource storageAccount 'Microsoft.Storage/storageAccounts@2021-04-01' = { name: 'mystorageaccount' location: resourceGroup().location sku: { name: 'Standard_LRS' } kind: 'StorageV2' }
```

Observations:

**Conciseness:** The Bicep code is noticeably shorter and less verbose than its ARM counterpart.

**Readability:** Bicep's structure feels more like traditional programming languages, making it easier to read and understand, especially for developers familiar with other scripting or programming languages.

**Directness:** Bicep eliminates the need for extraneous elements like $schema and contentVersion, focusing solely on the resource definition.

**Natural Syntax:** Functions like resourceGroup().location feel more intuitive in Bicep, aligning closely with their intended function.

It's evident from this comparison why many developers and infrastructure professionals are finding Azure Bicep a welcome change from ARM templates.
