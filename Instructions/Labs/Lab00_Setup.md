---
lab:
    title: 'Lab 0: Validate lab environment'
    module: 'Course introduction'
---

# Lab 0: Validate lab environment

**WWL Tenants - Terms of Use**
If you are being provided with a tenant as a part of an instructor-led training delivery, please note that the tenant is made available for the purpose of supporting the hands-on labs in the instructor-led training. 
Tenants should not be shared or used for purposes outside of hands-on labs. The tenant used in this course is a trial tenant and cannot be used or accessed after the class is over and is not eligible for extension. 
Tenants must not be converted to a paid subscription. Tenants obtained as a part of this course remain the property of Microsoft Corporation and we reserve the right to obtain access and repossess at any time. 

## Scenario

Bellows College is an educational organization with multiple campuses and programs. Many of Bellow Colleges instructors and administrators need to attend events, and purchase items. Historically tracking these expenses has been a challenge.

Campus administration would like to modernize their expense reporting system where employees submit expenses. 

Throughout this course, you will build applications and perform automation to enable Bellows College employees to manage expenses.

In this Module 1 lab, you will acquire a Power Platform trial and access the Power Platform admin center. In the admin center, you will then create a **Practice** environment that you will perform the majority of your lab work in.


## Exercise 1 – Setup

### Task #1 - Verify your Microsoft Power Platform trial tenant

1.  Verify that you have your **Microsoft 365 credentials** from the Authorized Lab Host available. 

2.  In a new browser tab, navigate to `https://make.powerapps.com`

3.  Enter the `email address` provided by the Authorized Lab Host. 

4.  Select **Sign in**. 

5.  Enter the `password` provided by the Authorized Lab Host. 

6.  Optionally, select **Yes** to stay signed in.

7.  If prompted, enter `0123456789` for **Phone number** and select **Submit**.

8.  **Refresh** the tab and verify the **Dev One** environment is selected under **Environment** in the top right. 



## Exercise 2 - Import Fabrikam solutions

In this exercise, you will import the main solution into the **Dev One** environment.

### Task 1.1 – Main solution

1.  Navigate to `https://make.powerapps.com`

1.  Make sure you are in the **Dev One** environment.

1.  Select **Solutions**.

1.  Select **Import solution**.

1.  Select **Browse** and locate the **FabrikamEnvironmental_1_1_11_3.zip** file and select **Open**.

    > **Note:** This file is located in the **Allfiles/Labs/** folder on GitHub repo.

    ![Solution to import.](../media/solution-to-import.png)

1.  Select **Next**.

1.  Select **Next** again.

1.  Select **Continue**.

1.  **Wait** while connections are created.

    ![Connections for import of solution.](../media/connections-for-solution.png)

1.  Select **Next**.

1.  Select **Import**.

    The solution will import in the background. This may take a few minutes.

    ![Solution imported.](../media/solution-imported.png)

    > **Alert:** Wait until the solution has finished importing before continuing to the next step.

1.  When the solution has imported successfully, open the **Fabrikam Environmental** solution.

1.  In the solution, select the **Overview** page.

    ![Overview.](../media/solution-overview.png)

1.  Select **Publish all customizations**.


## Exercise 2 - Import data

In this exercise, you will import data the into the **Dev One** environment using the Configuration Migration Tool and import Outcome rows into your Microsoft Dataverse environment using a dataflow.

### Task 2.1: Download and install Power Platform CLI

1.  Download the Power Platform CLI `https://aka.ms/PowerAppsCLI`

1.  Open **powerapps-cli-1.0.msi** to install the CLI tools.

1.  Use the setup wizard to complete the setup and select **Finish**.

1.  Open a **Command Prompt**.

1.  Verify Power Apps CLI is installed.

    `pac install latest`


### Task 2.2 - Import data with the Configuration Migration Tool

1.  Open a **Command Prompt**.

1.  Launch the **Configuration Migration Tool** using the following command:

    `pac tool cmt` 

    ![Configuration Migration Tool.](../media/configuration-migration-step1.png)

1.  Select **Import data**.

1.  Select **Continue**.

1.  Select **Office 365** for *Deployment Type*.

1.  Check **Display list of available organizations**.

1.  Check **Show Advanced**.

1.  Select **Don't know** for *Online Region*.

1.  Enter your Microsoft 365 tenant credentials.

    ![Configuration Migration Tool Login page.](../media/configuration-migration-step2.png)

1.  Select **Login**.

    ![Configuration Migration Tool select environment.](../media/configuration-migration-step3n.png)

1.  Choose the **Dev One** environment.

1.  Select **Login**.

    ![Configuration Migration Tool select data file.](../media/configuration-migration-step4.png)

1.  Select the ellipsis (...) menu and locate and select **Fabrikam Environment data.zip** file.

    > **Note:** This file is located in the **Allfiles/Labs/** on GitHub.

1.  Select **Open**. The data file will be validated.

1.  Select **Import Data**. The import process will take approximately a minute.

1.  Select **Exit**.

1.  Select the **X** to close the Configuration Migration Tool.


### Task 2.3 – Load Outcome Excel file to OneDrive

1.  Navigate to the Power Apps Maker portal `https://make.powerapps.com`

1.  Select the **Waffle** button in the upper left corner to change applications and select **OneDrive**. (It may take a moment for your OneDrive to be set up. Select **Your OneDrive is ready** when you see it on the screen.)

1.  Select **+ Add new** and select **Files upload**.

1.  Locate and select the **Outcome data.xlsx** file and select **Open**.

    > **Note:** This file should be located in the **Allfiles/Labs/** folder on GitHub repo.


### Task 2.4 – Create a dataflow to import Outcomes

1.  Navigate to the Power Apps Maker portal `https://make.powerapps.com`

1.  Make sure you are in the **Dev One** environment.

1.  Select **Tables** from the left navigation menu.

1.  Select **Import** from the action menu, then select **Import data**.

1.  In the **Choose data source** dialog, select **Excel workbook**.

1.  Select **Browse OneDrive**. If prompted, sign in with your Microsoft 365 credentials.

1.  Select the **Outcome data.xlsx** file.

1.  Select **Next**.

1.  Check the box next to **Table1**.

1.  Select **Next**. Do not navigate away from this page.

1.  Select the first three **Do Not Modify** columns. Tip: You can hold **Ctrl** on the keyboard and click with the mouse to select multiple columns.

1.  On the **Home** tab of the ribbon, select **Remove columns** to remove these three columns.

1.  Select the **Estimated Completion Date** column.

1.  Right-click on the **Estimated Completion Date** column and select **Replace values**.

1.  Enter `null` for **Value to find**.

1.  For **Replace with**, enter a date in three months time. Use date format **MM/DD/YYYY**.

1.  Select **OK**. The Estimated Completion Dates should show the date chosen.

1.  Select **Next**.

1.  Select **Load to existing table**.

1.  Select **contoso_outcome** from the **Destination table** drop-down.

1.  Under **Column mapping**, map **Estimated Completion Date**, **Goal**, **Outcome Description**, **Outcome Title**, and **Target Aim** to their corresponding destination columns.

1.  Select **Next**.

1.  Select **Refresh manually**.

1.  Select **Publish**.


### Task 2.5 – Test Your work

1.  Navigate to the Power Apps Maker portal `https://make.powerapps.com`

1.  Select **Tables**.

1.  Locate and open the **Outcome** table.

1.  You should see all the imported **Outcome** rows.

1.  In the Maker portal, select **Apps** from the left navigation.

1.  For the **Environmental Project Delivery** model-driven app, select the ellipsis **...** and select **Play**, signing in with your Microsoft 365 credentials if prompted.

1.  In the left navigation of the app, select **Outcomes**.

1.  The imported **Outcome** records should be in the view.

1.  Select the title to open one of the imported **Outcome** records.

1.  Verify the **Estimated Completion Date** column is set to the future date.

1.  Verify the **Outcome Lifecycle** business process flow is visible at the top of the form.
