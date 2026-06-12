---
title: "Launching app from menu giving different results from launching it from terminal."
date: 2009-08-02
forum: General Help
---

### Post by nbtrap on 2009-08-02
I've installed the Shorter Oxford English Dictionary 6 under Wine, and I'd like to attach its launch command to my F9 key. However, after binding the same command that launches the program from the kde menu to F9, I press F9, the window pops up and stays black. It's like it stops loading.

Here's the command I run:
env WINEPREFIX="/home/nathan/.wine" wine "C:\Program Files\SOED6\SOED6.exe"

or just:
wine "C:\Program Files\SOED6\SOED6.exe"


Now when I launch the program from my menu or Desktop shortcut, here's my output:

```

fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0xe8a51c,0x00000004,0xe8a518) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0xe89408): Stub!
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0xe89164,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0xe88ce4,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x5f5710, 0xe69d18) stub
fixme:psapi:EnumPageFilesA (0x5f5710, 0xe34634) stub
fixme:userenv:GetProfileType 0xe822b0
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0xe9f93c): Stub!
err:rpc:I_RpcGetBuffer no binding
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
E: context.c: waitpid(): No child processes
ALSA lib ../../../src/pcm/pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:imm:ImmReleaseContext (0x10034, 0x136918): stub

```

To see what the window looks like, see the first attached image.


Now, when I run the same command from a terminal or from the keybinding, I get an almost identical output:

```
nathan@Nathan-Linux:~$ env WINEPREFIX="/home/nathan/.wine" wine "C:\Program Files\SOED6\SOED6.exe"
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0xe8a51c,0x00000004,0xe8a518) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0xe89408): Stub!
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0xe89164,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0xe88ce4,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x5f5710, 0xe69d18) stub
fixme:psapi:EnumPageFilesA (0x5f5710, 0xe34634) stub
fixme:userenv:GetProfileType 0xe822b0
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0xe9f93c): Stub!
err:rpc:I_RpcGetBuffer no binding
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
E: context.c: waitpid(): No child processes
ALSA lib ../../../src/pcm/pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.

```
To see what the window looks like, see the second attached image.


Now as far as I can tell, the only difference in the output is the very bottom line:

```
fixme:imm:ImmReleaseContext (0x10034, 0x136918): stub
```

This line does not appear when I attempt to launch the program from the terminal.

I've also tried a number of different commands and combinations, but I'm getting the same results every time: the program only completely launches when launched from the menu or Desktop shortcut. What could possibly be causing this?

---

### Post by nbtrap on 2009-08-06
Bump.

---

### Post by martinbaselier on 2009-08-06
Your first post is quite hard to read, because you've written all the text inside code tags. 

If I understand correctly, the program works from the shortcut in the menu, but not when running directly or creating your own launcher.

The solution is probably available in the menu entry. I don't know exactly where the wine entries are saved. I believe they are in 
~/.local/share/applications/wine$


to find it, try this:
find * | grep -i NAMEOFTHEPROGRAM | grep -i .desktop

If you've found the file, you can take a look inside to find the correct command.

---

### Post by nbtrap on 2009-08-06
The command to launch from the file in ~/.local/share/applications/wine is the exact same used to launch from the menu, and the exact same command that doesn't work when I launch from the terminal. Any other ideas?

---

### Post by nbtrap on 2009-08-06
Bump.

---

### Post by dcstar on 2009-08-06
> **nbtrap said:**
> The command to launch from the file in ~/.local/share/applications/wine is the exact same used to launch from the menu, and the exact same command that doesn't work when I launch from the terminal. Any other ideas?

A terminal environment is not exactly the same as a desktop environment, various things are set when you launch a terminal process (and the terminal itself is another difference).

It could be very difficult to pinpoint the particular incompatible setting that is causing the problem.

---

