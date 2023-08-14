# Resolving the "Disk Quota Exceeded" Error

This guide aims to help users who have encountered the "disk quota exceeded" error on shared computing systems. Below, you'll find the error message, an explanation, and step-by-step instructions to resolve the issue.

## Error Message

The following error may be encountered:

```
OSError: [Errno 122] Disk quota exceeded
```

This error may indicate that the disk space allocated to the user or group has been exceeded.

## Solution

### Step 1: Check Disk Quota

Run the following command to check your current disk quota and usage:

```
quota
```

### Step 2: Find Files with Wrong Group Ownership

Use this command to find files that may have the wrong group ownership:

```
lfs find ~/projects/*/ -group $USER
```

### Step 3: Change Ownership of Files

If you find files with incorrect ownership, you can change their ownership with the following command:

```
chown -h -R $USER:your_group_name -- ~/projects/your_project_path/
```

Replace `your_group_name` and `your_project_path` with the appropriate values.

**Note:** This command can take some time if there are many files and directories.

### Step 4: Set Permissions (Optional)

Set the correct permissions for your project directories:

```
chmod 2770 ~/projects/def-professor/
chmod 2700 ~/projects/def-professor/$USER
```

### Step 5: Verify the Changes

After the `chown` command completes, you can rerun Step 2 to ensure no files are listed with incorrect ownership.

## Additional Resources

- Check with your system's documentation or support team for specific guidelines.
- If you encounter any issues, consider reaching out to your system administrator or support team.

## Contributing

Feel free to open an issue or submit a pull request if you have additional insights or corrections. Your contributions are welcome!
