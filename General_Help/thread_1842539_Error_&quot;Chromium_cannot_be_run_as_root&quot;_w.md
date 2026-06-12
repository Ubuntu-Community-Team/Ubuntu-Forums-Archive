---
title: "Error &quot;Chromium cannot be run as root&quot; when using Wireshark"
date: 2011-09-11
forum: General Help
---

### Post by ditaya on 2011-09-11
While trying to download the wireshark manual, the above error message pops up.

How do I fix this?

Thanks

Using Ubuntu 11.04 (64-bit) on a Dell XPS 15z.

EDIT: removed the screenshot since it contained some IP addresses!

---

### Post by haqking on 2011-09-11
download the manual direct  from the web rather than through wireshark.

you are running wireshark as root and i suspect that chromium is its default browser.

get it here [http://www.wireshark.org/docs/](http://www.wireshark.org/docs/)

or dont run as root and download it that way ;-)

---

### Post by ditaya on 2011-09-11
> **haqking said:**
> download the manual direct  from the web rather than through wireshark.

you are running wireshark as root and i suspect that chromium is its default browser.

get it here [http://www.wireshark.org/docs/](http://www.wireshark.org/docs/)

Yes, I am running Wireshark as root. Not sure of the latter part. However Chromium is NOT default browser on my laptop. 

Is there any chance changing the default browser for wireshark to Firefox, for instance? :-|

Shall download the manual directly from the link you've provided.

---

### Post by haqking on 2011-09-11
> **ditaya said:**
> Yes, I am running Wireshark as root. Not sure of the latter part. However Chromium is NOT default browser on my laptop. 

Is there any chance changing the default browser for wireshark to Firefox, for instance? :-|

Shall download the manual directly from the link you've provided.

edit menu, preferences and change the browser choice to firefox

oh and running Wireshark as root is not the recommended way, any reason you need to or think you need to ?

---

### Post by ditaya on 2011-09-11
> **haqking said:**
> edit menu, preferences and change the browser choice to firefox

I don't see the option of changing the web browser when I go to edit--->preferences. Also I do need to run wireshark as a "root" user, so running it as normal user is not an option unfortunately! :)

---

### Post by haqking on 2011-09-11
> **ditaya said:**
> I don't see the option of changing the web browser when I go to edit--->preferences. Also I do need to run wireshark as a "root" user, so running it as normal user is not an option unfortunately! :)


most users think they need to however often dont, see here from wireshark wiki:

**Administrator/root account not required!**

 Many Wireshark users think that Wireshark requires a root/Administrator account to work with. 
That's  not a good idea, as using a root account makes any exploit far more  dangerous: a successful exploit will have immediate control of the whole  system, compromising it completely. 
First  of all, most Wireshark functions can always be used with a (probably  very limited) user account. In particular, the protocol dissectors which  have shown most of the security related bugs do not need a root  account! 
Only  capturing (and gathering capture interface information) may require a  root account, but even that can usually be "circumvented", see [CaptureSetup/CapturePrivileges]("http://wiki.wireshark.org/CaptureSetup/CapturePrivileges") for details how to do so. 
 
**Protect Yourself!**

 There are some things you can do: 

[LIST]
[*]**Always update to the latest Wireshark version** available as bugs are fixed frequently. You can join the announce mailing list to stay informed about new versions. 
[*]**Don't run Wireshark as root/Administrator!** See [CaptureSetup/CapturePrivileges]("http://wiki.wireshark.org/CaptureSetup/CapturePrivileges") for details how to do so. 
[*]**Analyze capture files in an uncritical environment.** You may create a special (limited) user account or even use a dedicated machine for this task. 
[*]Use  a small capture tool which is less likely affected by security bugs,  e.g.: tcpdump or dumpcap) and transfer the capture file to the  uncritical environment mentioned above 
[*]The [SampleCaptures]("http://wiki.wireshark.org/SampleCaptures")  wiki page collects capture files for automated tests. If you have a  capture file with an undecoded protocol help the developers and attach  the file to that page. 
[/LIST]

Also go to edit menu, preferences and then user interface and put *firefox %s* into the web browser command.

---

### Post by ditaya on 2011-09-11
> **haqking said:**
> most users think they need to however often dont, see here from wireshark wiki:

**Administrator/root account not required!**

 Many Wireshark users think that Wireshark requires a root/Administrator account to work with. 
That's  not a good idea, as using a root account makes any exploit far more  dangerous: a successful exploit will have immediate control of the whole  system, compromising it completely. 
First  of all, most Wireshark functions can always be used with a (probably  very limited) user account. In particular, the protocol dissectors which  have shown most of the security related bugs do not need a root  account! 
Only  capturing (and gathering capture interface information) may require a  root account, but even that can usually be "circumvented", see [CaptureSetup/CapturePrivileges]("http://wiki.wireshark.org/CaptureSetup/CapturePrivileges") for details how to do so. 
 
**Protect Yourself!**

 There are some things you can do: 

[LIST]
[*]**Always update to the latest Wireshark version** available as bugs are fixed frequently. You can join the announce mailing list to stay informed about new versions. 
[*]**Don't run Wireshark as root/Administrator!** See [CaptureSetup/CapturePrivileges]("http://wiki.wireshark.org/CaptureSetup/CapturePrivileges") for details how to do so. 
[*]**Analyze capture files in an uncritical environment.** You may create a special (limited) user account or even use a dedicated machine for this task. 
[*]Use  a small capture tool which is less likely affected by security bugs,  e.g.: tcpdump or dumpcap) and transfer the capture file to the  uncritical environment mentioned above 
[*]The [SampleCaptures]("http://wiki.wireshark.org/SampleCaptures")  wiki page collects capture files for automated tests. If you have a  capture file with an undecoded protocol help the developers and attach  the file to that page. 
[/LIST]

Also go to edit menu, preferences and then user interface and put *firefox %s* into the web browser command.

Changing the default browser to Firefox did the trick! Thanks much for the heads-up. 

I am new to this wireshark application actually and it's part of my academic (university) curriculum - I was probably misinformed to run wireshark using root privileges. 

Shall try running as a limited user and see if I encounter any problems.. 

Thanks again. 

Cheers!

---

### Post by haqking on 2011-09-11
> **ditaya said:**
> Changing the default browser to Firefox did the trick! Thanks much for the heads-up. 

I am new to this wireshark application actually and it's part of my academic (university) curriculum - I was probably misinformed to run wireshark using root privileges. 

Shall try running as a limited user and see if I encounter any problems.. 

Thanks again. 

Cheers!


no problem, glad i could help.

Be careful with anything run as root, linux assumes you know exaclty what you are doing ;-)

remember to mark the thread as solved using thread tools to help others when searching for similar issues.

Cheers

regards

haqking

---

### Post by ditaya on 2011-09-11
> **haqking said:**
> no problem, glad i could help.

Be careful with anything run as root, linux assumes you know exaclty what you are doing ;-)

remember to mark the thread as solved using thread tools to help others when searching for similar issues.

Cheers

regards

haqking


Yup will keep that in mind!

Thanks again!

---

