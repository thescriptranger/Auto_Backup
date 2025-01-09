# Auto_Backup Bash Script

## Overview

The `Auto_Backup` Bash script is designed to back up files from source to destination directories based on an XML configuration file. 

> I use this script to backup all of my development work from Linux to my Synology NAS, along with my virtual machines, Homelab configurations, documents, and many other important things that I want double and triple backed up!  This is a bash alternative to my PowerShell Invoke-Backup script file

---

## Key Features

- **Configurable via XML:** Reads source and destination directories, included file extensions, and excluded file extensions from an XML file.
- **Incremental Backup:** Only backs up files modified since the last backup.
- **File Filtering:** Includes or excludes files based on extensions specified in the XML configuration file.
- **Logging:** Creates detailed logs of backup operations and removes logs older than 30 days.
- **Path Normalization:** Ensures compatibility with both local and network paths.
- **Error Handling:** Handles invalid paths and missing configuration gracefully.

---

## XML Configuration File

The script relies on an XML configuration file to define the backup sources, destinations, and file filtering rules. Here's an example:

```xml
<BackupSettings>
    <Sources>
        <Source>
            <SourcePath>C:\Users\Admin\Documents</SourcePath>
            <DestinationPath>\\MyNAS\Backup\Admin\Documents</DestinationPath>
        </Source>
        <Source>
            <SourcePath>C:\Users\Development</SourcePath>
            <DestinationPath>\\MyNAS\Backup\Admin\Development</DestinationPath>
        </Source>
    </Sources>
    <IncludedFileExtensions Enable="false">
        <Extension>.docx</Extension>
        <Extension>.xlsx</Extension>
        <Extension>.pdf</Extension>
    </IncludedFileExtensions>
    <ExcludedFileExtensions Enable="true">
        <Extension>.tmp</Extension>
        <Extension>.log</Extension>
        <Extension>.bak</Extension>
    </ExcludedFileExtensions>
</BackupSettings>
```
- **Sources:** Defines source directories to back up and their corresponding destinations. 
- **IncludedFileExtensions:** Files with these extensions are included in the backup if Enable is set to true. 
- **ExcludedFileExtensions:** Files with these extensions are excluded from the backup if Enable is set to true. 

---

## Prerequisites

### Dependencies
Ensure `xmllint` is installed for XML parsing (part of the `libxml2` package):

```bash
sudo apt install libxml2-utils
```

### Permissions

```bash
chmod +x auto_backup.sh
```

### Running the Script

1. Save the script to a `.ps1` file (e.g., `Invoke-Backup.ps1`).
2. Place the XML configuration file (e.g., `BackupConfig.xml`) in the same directory as the script.
3. Execute the script using the following command:

   ```bash
   ./auto_backup.sh

---

## Contribution

Contributions are welcome! Please fork the repository and submit pull requests to enhance functionality or fix bugs.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## Contact

For any questions, suggestions, or issues, please open an issue or contact **Script Ranger**.
