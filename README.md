# junit-test-case-analyzer
Analyze JUnit.xml test report.

## Parameters
### Inputs

|Parameter|Description|Required|Default|Type|
|:---|:---|:---|:---|:---|
|junit\_report_paths|JUnit.xml reports paths|True|-|string|


### Outputs

- Environment

|Env Name|Description|
|:-------|:----------|
|TOTAL\_TEST_CASES|Total Test Cases|
|TOTAL\_FAILURE_CASES|Total Failure Cases|
|TOTAL\_ERROR_CASES|Total Error Cases|
|TOTAL\_SKIPPED_CASES|Total Skipped Cases|
|TTOTAL\_SUCCESS_CASES|Total Success Cases|


- outputs

|Name|Description|
|:-------|:----------|
|steps.{your_step_id}.outputs.total_test_cases|Total Test Cases|
|steps.{your_step_id}.outputs.total_failure_cases|Total Failure Cases|
|steps.{your_step_id}.outputs.total_error_cases|Total Error Cases|
|steps.{your_step_id}.outputs.total_skipped_cases|Total Skipped Cases|
|steps.{your_step_id}.outputs.total_success_cases|Total Success Cases|



## Usage Examples

```
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Parse JUnit.xml
        id: parse_junit_report
        uses: ./
        with:
          junit_report_paths: "./test_reports/*.xml"
      - name: Ouputs
        run: |
          echo ${{ env.TOTAL_TEST_CASES }}
          echo ${{ env.TOTAL_FAILURE_CASES }}
          echo ${{ env.TOTAL_ERROR_CASES }}
          echo ${{ env.TOTAL_SKIPPED_CASES }}
          echo ${{ env.TOTAL_SUCCESS_CASES }}
```
