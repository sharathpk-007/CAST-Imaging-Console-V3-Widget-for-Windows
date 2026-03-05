# Imaging Console V3 Widget for Windows

## CAST Imaging Monitor for Windows (v3)

The Imaging console V3 widget for windows is a powerful, all-in-one desktop widget designed to
streamline the management and troubleshooting of your CAST Imaging environment on Windows. It
provides administrators and support personnel with a single, unified interface to monitor real-time
service health, access critical log files, browse application data, and directly inspect the configuration
database.

This tool eliminates the need to navigate complex file systems or use multiple applications,
dramatically accelerating issue diagnosis and simplifying the data collection process required for
support interactions.

**Key Features:**

- **Real-Time Service Dashboard:**
    Instantly view the live status of all core CAST Imaging services in a clear, color-coded list
    (Running, Stopped, Not Found). The dashboard automatically refreshes, allowing you to
    observe real-time changes and immediately identify services that are down.
- **Instant Log Viewer & Downloader:**
    Forget hunting for log files in different directories. Simply select a service to view its entire
    log file directly within the tool. A dedicated Refresh button lets you see new log entries as
    they happen, and the Download button packages the full log file for easy sharing with
    support agents.
- **Centralized Artifact Browser:**
    Navigate critical CAST Imaging folders like common-data, delivery, and deploy from dedicated
    tabs. This provides effortless access to:

```
o Delivery Packages: Browse delivered application versions and their folder structures.
```
```
o Common Data: Access shared analysis units and other essential data.
```
- **Direct Database Inspector:**
    Gain unprecedented insight by connecting directly to your CAST Imaging PostgreSQL
    database. The database tab allows you to:

```
o Browse key schemas like aip_config, aip_node, analysis_node, and control_panel.
```
```
o View the contents of any table to inspect configurations, check settings, or verify
data.
```
```
o Execute custom SELECT queries for advanced diagnostics.
This feature is invaluable for sharing precise environment settings and configuration
details with CAST Support, ensuring they have everything they need to resolve your
case quickly.
```

**How It Empowers You:**

- Faster Troubleshooting: Correlate a stopped service with its log file in seconds.
- Streamlined Support Interaction: Gather all necessary logs, data folders, and database
    configuration details from one place, ensuring support agents receive complete and accurate
    information every time.
- Proactive Monitoring: Understand the health of your Imaging stack at a glance, allowing you
    to spot potential issues before they impact users.
- Centralized Control: Manage your entire CAST Imaging environment from a single, intuitive
    application built for efficiency.

## Getting Started & Installation

The CAST Imaging console V3 widget for windows is a standalone, portable application designed for
ease of use and rapid deployment. It does not require a traditional installation process, registry
modifications, or system-level dependencies. This ensures that it can be run immediately without
altering your system configuration.

1. Double click on the **Imaging_Console_V3_Win_Widget_1.1.exe
2.** Provide the **config-all.conf** file that **is** present inside **com.castsoftware.imaging.console.3.X** which
you have configured for the installation


3. Click on the Execute & Refresh data to start using the tool.
4. You can navigate through the tabs to get the respective details and download them directly.
5. Navigate to the **Database** tab.

In the **Connection Details** section at the top, fill in the following fields with the information for your
PostgreSQL instance:

```
o Host: The server address (e.g., localhost).
```
```
o Port: The port number your database is listening on (e.g., 2284 ).
```
```
o Database Name: The name of the database (e.g., postgres).
```
```
o Username: A valid database user (e.g., operator).
```
```
o Password: The corresponding password for the user.
```

**Establish the Connection**

```
Click the Connect button located on the top right.
```
```
Look at the Status bar directly below the connection details. Upon success, it will turn green
and display a message similar to: Status: Connected to postgres on localhost:2284.
```
```
o The Connect button will now be disabled, and the Disconnect button will become
active.
```
**Choose the Target Schema**

```
Once connected, the Select Schema dropdown menu will be enabled.
```
```
Click the dropdown and select the schema you wish to inspect. Common schemas include:
```
```
o aip_config
```
```
o aip_node
```
```
o analysis_node
```
```
o control_panel
```
2. After selecting a schema, the **Tables** list below will automatically populate with all available
    tables within that schema.

**Step 4: View Table Data with a Single Click**

1. In the **Tables** list, simply **click on the name of the table** whose data you want to see
    (e.g., databasechangelog or properties).
2. **The tool will automatically execute a SELECT * query for the selected table.**
3. The full contents of that table will immediately appear in the **Query Results / Table**
    **Data** panel at the bottom of the screen. You can use the scrollbars to view all rows and
    columns.

## System Requirements & Limitations

The Imaging console V3 widget for windows is a powerful tool specifically designed for **single-server
deployments** of Imaging Console on Windows. To ensure full functionality, it is essential to
understand the following architectural requirement:

**Single-Host Architecture**

The core design of this tool relies on a **single config-all.conf file** to discover and manage the
environment. This means that all Imaging Console components (Authentication, Console,
Dashboards, Viewer services, etc.) **must be running on the same local machine or server where this
widget is executed.**


**This limitation impacts several key features:**

- **Service Monitoring:** The tool uses local system calls (psutil) to check the status of Windows
    services. It cannot monitor or manage services running on a remote server.
- **Log File Access:** All log file paths are resolved based on
    the INSTALL_DIR and DATA_DIR variables found within the local config-all.conf file. The tool
    can only access logs stored on the local file system.
- **Data Folder Browsing:** The Common-data and Delivery tabs function by reading local
    directory paths. They cannot browse file systems on other machines unless those paths are
    accessible via a mapped network drive or a UNC path from the host machine.

While the **Database Inspector** tab _can_ connect to a remote PostgreSQL database (by providing a
remote hostname), the primary and intended use case for this monitoring suite is for an all-in-one
installation. If your CAST Imaging environment is distributed across multiple servers, this tool should
be run on each server individually to monitor its local components.


