# Missing Value Imputation

**ID**: `imputation`  
**Version**: 1.0.0  
**Category**: preprocessing  
**Author**: CauldronGO Team

## Description

Impute missing values using various methods

## Runtime

- **Type**: `python`
- **Script**: `imputation.py`

## Inputs

| Name | Label | Type | Required | Default | Visibility |
|------|-------|------|----------|---------|------------|
| `input_file` | Input File | file | Yes | - | Always visible |
| `columns` | Columns to Impute | column-selector (multiple) | No | - | Always visible |
| `method` | Imputation Method | select (knn, simple, iterative, constant) | Yes | knn | Always visible |
| `k` | Number of Neighbors (KNN) | number (min: 1, max: 20, step: 1) | No | 5 | Visible when `method` = `knn` |
| `strategy` | Simple Strategy | select (mean, median, most_frequent) | No | mean | Visible when `method` = `simple` |
| `fillValue` | Fill Value (Constant) | number | No | 0 | Visible when `method` = `constant` |
| `iterations` | Max Iterations (Iterative) | number (min: 1, max: 100, step: 1) | No | 10 | Visible when `method` = `iterative` |

### Input Details

#### Input File (`input_file`)

Data file with missing values


#### Columns to Impute (`columns`)

Select columns to impute (empty = all columns)

- **Column Source**: `input_file`

#### Imputation Method (`method`)

Method to use for imputation

- **Options**: `knn`, `simple`, `iterative`, `constant`

#### Number of Neighbors (KNN) (`k`)

Number of neighbors for KNN imputation


#### Simple Strategy (`strategy`)

Strategy for simple imputation

- **Options**: `mean`, `median`, `most_frequent`

#### Fill Value (Constant) (`fillValue`)

Value to use for constant imputation


#### Max Iterations (Iterative) (`iterations`)

Maximum iterations for iterative imputation


## Outputs

| Name | File | Type | Format | Description |
|------|------|------|--------|-------------|
| `imputed_data` | `imputed.data.txt` | data | tsv | Data with imputed values |

## Requirements

- **Python**: >=3.11
- **Packages**:
  - numpy>=1.24.0
  - pandas>=2.0.0
  - scikit-learn>=1.3.0

## Example Data

This plugin includes example data for testing:

```yaml
  input_file: diann/imputed.data.txt
  columns_source: diann/imputed.data.txt
  columns: [C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-IP_01.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-IP_02.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-IP_03.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-MockIP_01.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-MockIP_02.raw C:\Raja\DIA-NN searches\June 2022\LT-CBQCA-Test_DIA\RN-DS_220106_BCA_LT-MockIP_03.raw]
  method: knn
  k: 5
```

Load example data by clicking the **Load Example** button in the UI.

## Usage

### Via UI

1. Navigate to **preprocessing** → **Missing Value Imputation**
2. Fill in the required inputs
3. Click **Run Analysis**

### Via Plugin System

```typescript
const jobId = await pluginService.executePlugin('imputation', {
  // Add parameters here
});
```
