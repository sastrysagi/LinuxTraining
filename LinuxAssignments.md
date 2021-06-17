# Linux Assignments
---

## Pre-Requisites Install Linux in Machine


1. Enabled [WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10#step-4---download-the-linux-kernel-update-package)
2. Installed Ubuntu, Kali (CLI only)
3. Installed Oracle Virtual BOx
4. Installed Ubuntu 21.04 in the Oracle Virtual Box (GUI)
5. Planning to explore options with DOcker as well


---

## Assignment 1 - Create Multi Boot USB
**Created multiboot USB using [ventoy](www.ventoy.net) tool**
*Majority of the code was written in C and minor BASH Script is also there. source code is openly available in [github](https://github.com/ventoy/Ventoy)*
### Small Writeup on the tool
Ventoy is an open source tool to create bootable USB drive for ISO/WIM/IMG/VHD(x)/EFI files.
With ventoy, you don't need to format the disk over and over, you just need to copy the ISO/WIM/IMG/VHD(x)/EFI files to the USB drive and boot them directly.
You can copy many files at a time and ventoy will give you a boot menu to select them.
x86 Legacy BIOS, IA32 UEFI, x86_64 UEFI, ARM64 UEFI and MIPS64EL UEFI are supported in the same way.
Most type of OS supported (Windows/WinPE/Linux/Unix/VMware/Xen...)

---

## Assignment 2 - WOL (wake-up on Lan)
Unable to test it due to lack of infrastructure. My Laptop doesn't carry with a RJ45 Jack.

---

## Assignment 3 - Delete all files in the linux folder including sub folders
To test this i created a folder in user home directroy called test and inside that i created several folders and files in a nested way. 
Commands used 

` mkdir -- for making directory `

` cd -- to change the directory `

` touch -- to create the blank files. `

Command used to explore the files and subdirectories in a tree fashion (similar to tree command in dos/windows)

` ls -R`

Command to delete all files and folders recursively we can use rm command with different flags

**r -- Recursive**

**f -- forcefully**

**v --verbose**

` rm -r -f -v /PATH-TO-DELETE `

in short we can use 

` rm -rfv /PATH-TO-DELETE`

---

## Assignment 4 - Change default run level

To check your current and previous runlevel use `runlevel` command:

To permanently change your runlevel on Ubuntu Linux edit the following line within `/etc/init/rc-sysinit.conf:`

`env DEFAULT_RUNLEVEL=2`

Another alternative on how to change a default runlevel on Ubuntu Linux is to edit Grub's default startup sequence. Locate /etc/default/grub file and edit line:

`GRUB_CMDLINE_LINUX=""`

To include your desired runlevel. For example to change default runlevel to 5 edit the above line to desired runlevel. For example to change to runlevel 5 insert:

`GRUB_CMDLINE_LINUX="5"`

and run Grub update command with administrative privileges:

`update-grub`

### Alternative way
Mapping between runlevels and systemd targets
```
   ┌─────────┬───────────────────┐
   │Runlevel │ Target            │
   ├─────────┼───────────────────┤
   │0        │ poweroff.target   │
   ├─────────┼───────────────────┤
   │1        │ rescue.target     │
   ├─────────┼───────────────────┤
   │2, 3, 4  │ multi-user.target │
   ├─────────┼───────────────────┤
   │5        │ graphical.target  │
   ├─────────┼───────────────────┤
   │6        │ reboot.target     │
   └─────────┴───────────────────┘
 ```  
**Now, to just change the "runlevels" in > 16.04, you can use for eg:**

sudo systemctl isolate multi-user.target
To make this the default "runlevel", you can use:
```
sudo systemctl enable multi-user.target
sudo systemctl set-default multi-user.target

```
### From man systemctl

   isolate NAME
       Start the unit specified on the command line and its dependencies and stop all others. If
       a unit name with no extension is given, an extension of ".target" will be assumed.

       This is similar to changing the runlevel in a traditional init system. The isolate command
       will immediately stop processes that are not enabled in the new unit, possibly including
       the graphical environment or terminal you are currently using

---

## Assignment 5 - Change UMASK value in Linux (Ubuntu 21.04)
By using `umask` command we can find out the value of the masking for the user
using `umask 0003` we can set the value of umask. 

---

## Assignment 6 - find the permission set to the downloaded files
For me the files are stored with the permission set by umask value. 

---

## Assignment 7 - Find the path of the temporary files of the browser
In my Ubuntu 21.04 `~/.mozilla/firefox/*.default/Cache` is the location i observe the browser cache and the permission is 700 i.e. 

`-rwx------`

---
## Assignment 8 - Find Process id of init
```
pidof init

```

`pidof` provides the porcess id of given program 


