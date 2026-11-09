# LLM-generated bash commands fail on Windows due to PowerShell enforcement

## Description

I am using Kimi CLI on Windows with Git Bash installed. When the AI generates shell commands, it frequently uses bash-specific syntax (e.g., `&&` for chaining commands, `export` for environment variables, or standard piping).

However, the tool appears to strictly use PowerShell to execute these commands, which results in syntax errors because PowerShell does not support these standard bash operators in the same way.

## Reproduction Script
1. Start a Kimi CLI session on Windows (where Git Bash or WSL is installed).
2. Ask the AI to run a simple chained command, for example:
   ```bash
   export TEST_VAR="hello" && echo $TEST_VAR
   ```

## Actual Behavior

The command execution fails with a PowerShell error, such as:
```
The term 'export' is not recognized as the name of a cmdlet, function, script file, or operable program.
```
Or errors related to the `&&` operator depending on the PowerShell version.

## Expected Behavior

The CLI should either:
1. Automatically detect that I have a bash-compatible shell (like Git Bash, MSYS2, or WSL) available on my system and use it.
2. Provide a way to configure the tool to use bash instead of PowerShell so that LLM-generated commands execute successfully.
