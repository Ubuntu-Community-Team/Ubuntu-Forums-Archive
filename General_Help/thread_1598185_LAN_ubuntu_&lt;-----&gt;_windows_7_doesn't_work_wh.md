---
title: "LAN ubuntu &lt;-----&gt; windows 7 doesn't work why?"
date: 2010-10-16
forum: General Help
---

### Post by psihokiller4 on 2010-10-16
don't know where to ask ...


I'm using gnome commander most of time I could copy files from win 7 few weeks ago now...
when I enter work group I see computers (win7 ) trough LAN but cannot access it as other windows users can do it normally if I from dual boot (win xp(32bit)) connect it does normally

why linux can't transfer data or copy files to win 7?

I used Network Tools
If I traceroute I see:
- my self
- 3X gateway
- BSN-access.dsl.siol.net

if I portscan
I see 7 opened ports

if I ping to computer I wish to access I get average 0.30 ms witch means I should access to win7(64bit) with linux(ubuntu)(32bit) (no?)

uname -a

```
Linux dusanlaptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
```it nothing makes sense to me
need help

---

### Post by luvshines on 2010-10-16
Are you trying to access the Windows share ??

Have you tried accessing it through nautilus

---

### Post by psihokiller4 on 2010-10-16
I just tried
had to found out what that is:

nautilus
[http://ubuntuforums.org/showthread.php?t=309772](http://ubuntuforums.org/showthread.php?t=309772)

if I'm correct

well I get message from gnome commander:
```
Listing failed: Internal error
```and from nautilus
```
**Unable to mount location**

Failed to retrieve share list from server
```but we don't have server we have only each computer as it's own master if I may say it that way



and actually I'm trying to access windows share

---

### Post by thuntley on 2010-10-16
Did the permissions change on your Win7 shares?  Or maybe a Windows Update caused changes in the firewall or sharing settings?

---

### Post by luvshines on 2010-10-16
> **psihokiller4 said:**
> 
well I get message from gnome commander:
```
Listing failed: Internal error
```and from nautilus
```
**Unable to mount location**

Failed to retrieve share list from server
```but we don't have server we have only each computer as it's own master if I may say it that way

and actually I'm trying to access windows share

It will always say 'server', even for standalone machine which shares data :)

Just try can you access it with terminal:
```
## List the share. Drop -U <un>%<pwd> if guest allowed
smbclient -L <server-ip> -U<username>%<passwd>

## Access the shares. Drop -U <un>%<pwd> if guest allowed
smbclient //<server-ip>/<share-name> -U<username>%<passwd>

```

Also try doing this with server-name(if reachable through name), instead of ip

---

### Post by psihokiller4 on 2010-10-16
sorry me noob here don't get it


after 2.,4. line
bash: syntax error near unexpected token `newline'

we don't have password and
as I know new line can't be done to terminal and after that to execute command
[FONT=monospace]
[/FONT]```

## List the share. Drop -U <un>%<pwd> if guest allowed[FONT=monospace]
[/FONT]smbclient -L </*change data?*/> -U</*change data?*/>%</*what to change here?*/>

```

---

### Post by psihokiller4 on 2010-10-16
> **thuntley said:**
> Did the permissions change on your Win7 shares?  Or maybe a Windows Update caused changes in the firewall or sharing settings?

don't know about that all I know I see permissions now --------- so even root doesn't have access but windows doesn't know about these permissions to show to linux(linux version for permissions) so I guess all should have permission

---

### Post by luvshines on 2010-10-16
> **psihokiller4 said:**
> sorry me noob here don't get it

after 2.,4. line
bash: syntax error near unexpected token `newline'

we don't have password```

## List the share. Drop -U <un>%<pwd> if guest allowed[FONT=monospace]
[/FONT]smbclient -L </*change data?*/>

```

No problem, we are all here to learn :)
Without password, simply press ENTER when it asks for one

---

### Post by psihokiller4 on 2010-10-16
```
military@dusanlaptop:~$ ## List the share. Drop -U <un>%<pwd> if guest allowed
military@dusanlaptop:~$ smbclient -L <192.168.1.3>
bash: syntax error near unexpected token `newline'
military@dusanlaptop:~$ 
```

I still don't get it

what's wrong here

---

### Post by luvshines on 2010-10-16
> **psihokiller4 said:**
> ```
military@dusanlaptop:~$ ## List the share. Drop -U <un>%<pwd> if guest allowed
military@dusanlaptop:~$ smbclient -L <192.168.1.3>
bash: syntax error near unexpected token `newline'
military@dusanlaptop:~$ 
```

I still don't get it

what's wrong here

Oh, Ok !!
<...> is a general convention for a placeholder. When we write it this way, it stands for something to be replaced with actual value :)

For you it will be, smbclient -L 192.168.1.3

---

### Post by psihokiller4 on 2010-10-16
```

military@dusanlaptop:~$ smbclient -L 192.168.1.3
Enter military's password: 
Domain=[LIONESS] OS=[Windows 7 Ultimate 7600 Service Pack 2] Server=[Windows 7 Ultimate 6.1]

    Sharename       Type      Comment
    ---------       ----      -------
Error returning browse list: NT_STATUS_NOT_SUPPORTED
session request to 192.168.1.3 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

```

```

military@dusanlaptop:~$ smbclient //192.168.1.3/lioness
Enter military's password: 
Domain=[LIONESS] OS=[Windows 7 Ultimate 7600 Service Pack 2] Server=[Windows 7 Ultimate 6.1]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```

ok thanks

now I don't get it I heaved "lookup" at pc name so I gain the address so address has to be correct + it says windows and lioness for the IP so I really don't understand how IP name not present

---

### Post by luvshines on 2010-10-16
I have seen that error before but haven't seen a solution yet.

Can you try enabling netbios over tcp/ip:
[http://ttcshelbyville.wordpress.com/2009/12/17/enable-netbios-over-tcpip/](http://ttcshelbyville.wordpress.com/2009/12/17/enable-netbios-over-tcpip/)

---

### Post by psihokiller4 on 2010-10-16
thanks well that lead me to this:

[http://ubuntuforums.org/showthread.php?t=88206](http://ubuntuforums.org/showthread.php?t=88206)
[http://ubuntuforums.org/showthread.php?t=88206&page=7](http://ubuntuforums.org/showthread.php?t=88206&page=7)
[http://ubuntuforums.org/showthread.php?t=88206&page=6](http://ubuntuforums.org/showthread.php?t=88206&page=6)

I've read every word of it but couldn't make it work well it seems I'm still low lvl linux user and it'll be loooong time till I'll move someone else


if anyone knows how to help my problem please help

---

### Post by luvshines on 2010-10-16
We are already having similar discussions here:
[http://ubuntuforums.org/showthread.php?t=1597706](http://ubuntuforums.org/showthread.php?t=1597706)

See if Comment #8 helps

---

### Post by silverbullet763 on 2010-10-16
Do you know what version of samba your using. I found this information on another site:

**Error returning browse list: NT_STATUS_NOT_SUPPORTED**

       
                                This is annoying.  I&#8217;m attempting to get to my photos on my  Win 7 desktop from my Linux laptop.  It works in Win XP clients, but  smbclient is failing:[INDENT][evan@ehoffman ~]$ smbclient -L //192.168.10.105/ Enter evan's password: Domain=[EVAN-WOLFDALE7] OS=[Windows 7 Ultimate 7100] Server=[Windows 7 Ultimate 6.1]      Sharename       Type      Comment     ---------       ----      ------- Error returning browse list: NT_STATUS_NOT_SUPPORTED session request to 192.168.10.105 failed (Called name not present) session request to 192 failed (Called name not present) session request to *SMBSERVER failed (Called name not present) NetBIOS over TCP disabled -- no workgroup available [evan@ehoffman ~]$  [/INDENT]**Update**: This appears to be resolved in [Samba 3.4.3]("http://news.samba.org/releases/3.4.3/") ([release notes]("http://samba.org/samba/history/samba-3.4.3.html")).   Since there&#8217;s no RPM for 3.4.2 for FC11 I downloaded the source and  built it and tried the smbclient against my Win7 box and it worked fine.


This guy wasn't on ubuntu though. Link to bug report here [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/472681](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/472681)

Edit: This has supposedly been fixed in Lucid. What version of ubuntu are you on?

---

### Post by psihokiller4 on 2010-10-17
it works ok

1. what I've done I destroyed my machine (I couldn't even open SMB(network)) again I was angry at my self again even if I did .bac file it didn't work well propably I'll have to learn how to see links between files and how to do links

I was so angry that I did update system witch usually completelly destroyed my system but this time I used only main and source code wwitch once people recomended thanks to them :>>>>>

(but I still don't want to use too many updates as it could cause damage to my OS)

really thanks to people witch recommend long term releases (and explaining it) to people espacelly beginner users


now I can access 4 win7 computers and change data .... [SOLVED]

---

### Post by psihokiller4 on 2010-10-17
> **silverbullet763 said:**
> 
Do you know what version of samba your using

it didn't have installed samba at all (only names samba not what's here now)

now I have:

Package | Installed Version

samba-common | 2:3.4.0-3ubuntu5.7
samba-common-bin | 2:3.4.0-3ubuntu5.7
libwbclient0 | 2:3.4.0-3ubuntu5.7
python-smbc | 1.0.6-0ubuntu2
winbind | 2:3.4.0-3ubuntu5.7
smbclient | 2:3.4.0-3ubuntu5.7
nautilus-share | 0.7.2-12
libsmbclient | 2:3.4.0-3ubuntu5.7



> **silverbullet763 said:**
> 
Edit: This has supposedly been fixed in Lucid. What version of ubuntu are you on?

ubuntu 9.10

I hate licid
1. I couldn't change that s****d strange desktop environment
2. it has some sound issues witch are normal in this one for sound a new openal has a bug and I had to replace it and  linked it with someone elses help + don't know what he sad else to do that worked fine
(default every sound in game works only 1 second (and after that quiet) even if sound should work 8 seconds)
except music works normally maybie it supports only 1 file don't know

---

