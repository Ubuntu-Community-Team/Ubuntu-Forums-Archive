---
title: "Can't connect to TS Windows Server"
date: 2011-02-25
forum: General Help
---

### Post by rva1945 on 2011-02-25
I can connect in W XP with mstsc. But none of the Remote DEsktop clients in Ubuntu work (Gnome-rdp, Grdc remote desktop client, Remotedesktop client, etc.) they simply don't connect.

Then I tried wine mstsc.exe, I get a lot of output, this is the last line:

fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE

then when I enter the address inthe mstsc window

fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 0/00/0000, dlt (d/m/y): 0/00/0000
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10056 0x00000000
err:seh:setup_exception_record stack overflow 832 bytes in thread 0009 eip 601b85ee esp 00230ff0 stack 0x230000-0x231000-0x330000

and the mstsc freezes forever (I have to force quit it).

Help?

---

### Post by JRV on 2011-02-26
Try this:

```

sudo apt-get install rdesktop

```

Then:

```

rdesktop -f -u USERNAME -p PASSWORD -r sound:local HOSTNAME

```

---

### Post by rva1945 on 2011-02-26
> **JRV said:**
> Try this:

```

sudo apt-get install rdesktop

```Then:

```

rdesktop -f -u USERNAME -p PASSWORD -r sound:local HOSTNAME

```

rdesktop was already installed.

Done it, but I get:

Autoselected keyboard map en-us
ERROR: recv: Connection reset by peer

---

### Post by JRV on 2011-02-27
I can't duplicate the problem, have you successfully logged on to the XP machine from any other computer?

Everything I can think of to try I get a successful log-in or I get the "Autoselected keyboard map en-us" message and then nothing.

Are you using a firewall that could be blocking it?

---

### Post by rva1945 on 2011-02-27
> **JRV said:**
> I can't duplicate the problem, have you successfully logged on to the XP machine from any other computer?
 
Everything I can think of to try I get a successful log-in or I get the "Autoselected keyboard map en-us" message and then nothing.
 
Are you using a firewall that could be blocking it?
 
Well, I've been logging for months from the XP partition, that ceased to boot two days ago. I could never log from Ubuntu, and I can't do from the XP virtual machine. Maybe the Windows server doesn't accept the connection because it doesn't recognize the client as a Windows family member?

---

### Post by JRV on 2011-02-27
Well, I'm sorry but that is all I have, I am not very familiar with Wine or virtual machines.

---

### Post by dvdbrnds on 2011-02-27
Hi there,
  I myself am experiencing a similar situation where no matter what i do or how i rty and connect i get a dreaded ...

[FONT=System]ERROR: recv: Connection reset by peer[/FONT]

this issue is complicated by my ability to easily connect using a Virtual machine running on the same Ubuntu box. I took the liberty of doing some "wiresharking" to see if there was anything remiss.

The Connection request that was accepted from my Windows XP VM running in KVM showed this....

[COLOR=YellowGreen]0000  00 19 07 4e 40 80 00 21  5d 98 ed f2 08 00 45 00   ...N@..! ].....E.
0010  00 3b 00 51 40 00 7f 06  df ac 0a 0b 04 0c 0a c8   .;.Q@... ........
0020  02 e1 04 0b 0d 3d 44 42  6c fc 17 c7 52 84 50 18   .....=DB l...R.P.
0030  ff ff 55 2b 00 00 03 00  00 13 0e e0 00 00 00 00   ..U+.... ........
0040  00 01 00 08 00 01 00 00  00                        ........ .[/COLOR]       

And the Connection request that was denied directly from Ubuntu using rdesktop returned this...

[COLOR=YellowGreen]0000  00 19 07 4e 40 80 00 21  5d 98 ed f2 08 00 45 00   ...N@..! ].....E.
0010  00 5a e5 b0 40 00 40 06  39 2e 0a 0b 04 0c 0a c8   .Z..@.@. 9.......
0020  02 e1 9e 2a 0d 3d 33 ca  25 43 6e a7 dd 7e 80 18   ...*.=3. %Cn..~..
0030  00 2e 6a 0d 00 00 01 01  08 0a 00 01 c0 ec 00 00   ..j..... ........
0040  00 00 03 00 00 26 21 e0  00 00 00 00 00 43 6f 6f   .....&!. .....Coo
0050  6b 69 65 3a 20 6d 73 74  73 68 61 73 68 3d 62 72   kie: mst shash=br
0060  61 6e 64 65 73 64 0d 0a                            andesd..     [/COLOR]

The difference im noticing myself is that the rdesktop connection is sending a cookie and a hash including the username (brandesd) My network engineer thinks this isnt working for me because the unencrypted cleartext user id is getting refused outright by the server because of the security settings. this theory is corroborated by my ability to RDP form Ubuntu into an unsecured machine on the network.

that being said i have no idea what to do about any of it. I cant figure out where the config file i need to manipulate to force encryption is.

Thank you in advance for any light you can shed on the subject...

dvdbrnds

---

### Post by rva1945 on 2011-02-27
> **dvdbrnds said:**
> Hi there,
  I myself am experiencing a similar situation where no matter what i do or how i rty and connect i get a dreaded ...

[FONT=System]ERROR: recv: Connection reset by peer[/FONT]

this issue is complicated by my ability to easily connect using a Virtual machine running on the same Ubuntu box. I took the liberty of doing some "wiresharking" to see if there was anything remiss.

The Connection request that was accepted from my Windows XP VM running in KVM showed this....

[COLOR=YellowGreen]0000  00 19 07 4e 40 80 00 21  5d 98 ed f2 08 00 45 00   ...N@..! ].....E.
0010  00 3b 00 51 40 00 7f 06  df ac 0a 0b 04 0c 0a c8   .;.Q@... ........
0020  02 e1 04 0b 0d 3d 44 42  6c fc 17 c7 52 84 50 18   .....=DB l...R.P.
0030  ff ff 55 2b 00 00 03 00  00 13 0e e0 00 00 00 00   ..U+.... ........
0040  00 01 00 08 00 01 00 00  00                        ........ .[/COLOR]       

And the Connection request that was denied directly from Ubuntu using rdesktop returned this...

[COLOR=YellowGreen]0000  00 19 07 4e 40 80 00 21  5d 98 ed f2 08 00 45 00   ...N@..! ].....E.
0010  00 5a e5 b0 40 00 40 06  39 2e 0a 0b 04 0c 0a c8   .Z..@.@. 9.......
0020  02 e1 9e 2a 0d 3d 33 ca  25 43 6e a7 dd 7e 80 18   ...*.=3. %Cn..~..
0030  00 2e 6a 0d 00 00 01 01  08 0a 00 01 c0 ec 00 00   ..j..... ........
0040  00 00 03 00 00 26 21 e0  00 00 00 00 00 43 6f 6f   .....&!. .....Coo
0050  6b 69 65 3a 20 6d 73 74  73 68 61 73 68 3d 62 72   kie: mst shash=br
0060  61 6e 64 65 73 64 0d 0a                            andesd..     [/COLOR]

The difference im noticing myself is that the rdesktop connection is sending a cookie and a hash including the username (brandesd) My network engineer thinks this isnt working for me because the unencrypted cleartext user id is getting refused outright by the server because of the security settings. this theory is corroborated by my ability to RDP form Ubuntu into an unsecured machine on the network.

that being said i have no idea what to do about any of it. I cant figure out where the config file i need to manipulate to force encryption is.

Thank you in advance for any light you can shed on the subject...

dvdbrnds

Interesting. That would explain why I can't connect from Ubuntu RDesktop. But what happens with mstsc from the W XP virtual machine (Ubuntu the host, WXP the guest)? I'm trying to connect to a Windows Server in the office.

In that case, the connection ends due to timeout.

Regards

---

### Post by dvdbrnds on 2011-02-27
> **rva1945 said:**
> Interesting. That would explain why I can't connect from Ubuntu RDesktop. But what happens with mstsc from the W XP virtual machine (Ubuntu the host, WXP the guest)? I'm trying to connect to a Windows Server in the office.

In that case, the connection ends due to timeout.

Regards

The mstsc from the windows XP guest running on the Ubuntu 10.10 machine connects without fail to any and all versions of Windows i am trying to connect to. If i try and RDP natively from Ubuntu however it sends the cookie and i get the error.

---

### Post by dcstar on 2011-02-28
> **dvdbrnds said:**
> Hi there,
  I myself am experiencing a similar situation where no matter what i do or how i rty and connect i get a dreaded ...

[FONT=System]ERROR: recv: Connection reset by peer[/FONT]

..........
The difference im noticing myself is that the rdesktop connection is sending a cookie and a hash including the username (brandesd) My network engineer thinks this isnt working for me because the unencrypted cleartext user id is getting refused outright by the server because of the security settings. this theory is corroborated by my ability to RDP form Ubuntu into an unsecured machine on the network.

that being said i have no idea what to do about any of it. I cant figure out where the config file i need to manipulate to force encryption is.

Thank you in advance for any light you can shed on the subject...

dvdbrnds

Try installing the **tsclient** package as that allows a choice of RDP or RDPv5 protocols, and the latter might have better security that allows a connection.

---

### Post by rva1945 on 2011-02-28
> **dcstar said:**
> Try installing the **tsclient** package as that allows a choice of RDP or RDPv5 protocols, and the latter might have better security that allows a connection.
 
I have the TS client installed, and tried with both protocols, to no avail.
 
The server I'm trying to connect to is a Windows Server 2003 R2 (that's what appears in the log in window).
 
Thanks

---

### Post by dvdbrnds on 2011-02-28
> **rva1945 said:**
> I have the TS client installed, and tried with both protocols, to no avail.
 
The server I'm trying to connect to is a Windows Server 2003 R2 (that's what appears in the log in window).
 
Thanks


Thank you for the response. I have the tsclient installed and i receive the same error. I also installed the XRPD package and VNC trying to bridge through VNC as described in XRDP docs but no avail.

---

### Post by rva1945 on 2011-02-28
> **dvdbrnds said:**
> The mstsc from the windows XP guest running on the Ubuntu 10.10 machine connects without fail to any and all versions of Windows i am trying to connect to. If i try and RDP natively from Ubuntu however it sends the cookie and i get the error.
 
 
What really puzzles me is the fact that until last week I could connect when booting form the XP partition, which now it failed, thus I had to instal the XP in a VM with Virtualbox. I could never connect with any Ubuntu RDP or TS client. And now it seems as if wht Windows Server detects that the client is not a Windows family cient, although I run mstsc in a VM.
 
I think I should disable the Linux connection to Internet and try to set up a connection once in VM XP.

---

### Post by dcstar on 2011-03-01
> **rva1945 said:**
> What really puzzles me is the fact that until last week I could connect when booting form the XP partition, which now it failed, thus I had to instal the XP in a VM with Virtualbox. I could never connect with any Ubuntu RDP or TS client. And now it seems as if wht Windows Server detects that the client is not a Windows family cient, although I run mstsc in a VM.
 

It is possible that the Security on the Windows server may have been changed to only allow connections using methods the Linux RDP tool does not support.

Ask the people who maintain the Windows server if things changed recently.

---

### Post by rva1945 on 2011-03-01
> **dcstar said:**
> It is possible that the Security on the Windows server may have been changed to only allow connections using methods the Linux RDP tool does not support.
 
Ask the people who maintain the Windows server if things changed recently.
 
 
I found it: from inux clientes, I can connect to Windows Server 2003, but not to Windows Server 2003 R2.
 
That's it.

---

