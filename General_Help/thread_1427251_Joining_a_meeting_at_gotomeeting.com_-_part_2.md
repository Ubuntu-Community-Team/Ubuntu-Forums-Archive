---
title: "Joining a meeting at gotomeeting.com - part 2"
date: 2010-03-11
forum: General Help
---

### Post by altonbr on 2010-03-11
Continuation of this archived thread: [http://ubuntuforums.org/showthread.php?t=642095](http://ubuntuforums.org/showthread.php?t=642095)

I ran into the same problem, the inability to join a meeting via GoToMeeting, when two potential contracts both requested me to use it on the same day!

I received this error from their website:

> To join the Meeting, please use one of the following supported operating systems:
 * Windows® 7, Vista, XP, 2003 Server or 2000
 * Mac OS® X, Panther® 10.3.9, Tiger™ 10.4.5 or higher
For more information on system requirements, check out [GoToMeeting Frequently Asked Questions]("https://www2.gotomeeting.com/en_US/pre/faq3.tmpl#q1").

Since [ies4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") has been stale for a number of years and no longer compiles in Ubuntu, I thought I'd use [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59"), the Firefox Add-on, and trick the website into thinking I was using Internet Explorer.

The add-on helped me evade the OS detection script, but it prompted me with a Windows file I needed to run. It looks part XML, part binary blob.

Like any red-blooded Ubuntuian, I ran it through Wine, but recieved this:
> wine Desktop/AppCore.application
wine: Bad EXE format for Z:\home\brett\Desktop\AppCore.application

I've attached the screenshots and XML/binary blob (note: it was called AppCore.application, not AppCore.application.txt) for your perusal.

What another fellow suggested is using the cross-platform [Yugma]("http://www.yugma.com/"). Unfortunately, I'm not the one setting up the meetings.

---

### Post by altonbr on 2010-03-11
If I trick gotomeeting.com into thinking I'm running Firefox on a Mac, I get a screen that tells me I could download/install Java (which it is) and to run 'g2m_download.exe'.

Running it in Wine returns:
> $ wine Desktop/g2m_download.exe 
err:ntdll:NtQueryInformationToken Unhandled Token Information class 25!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (120000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 120000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 120000
fixme:crypt:CRYPT_CriticalExtensionsSupported unsupported critical extension "2.5.29.32"
fixme:crypt:CRYPT_CriticalExtensionsSupported unsupported critical extension "2.5.29.32"
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (120000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 120000
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 120000
err:ntdll:NtQueryInformationToken Unhandled Token Information class 25!
fixme:advapi:SetSecurityInfo stub
brett@evolution:~$ err:ntdll:NtQueryInformationToken Unhandled Token Information class 25!
fixme:advapi:SetSecurityInfo stub
err:ntdll:NtQueryInformationToken Unhandled Token Information class 25!
err:shell:SHGetFileInfoW pidl is null!
err:shell:SHGetFileInfoW pidl is null!
err:shell:SHGetFileInfoW pidl is null!
err:shell:SHGetFileInfoW pidl is null!
err:shell:SHGetFileInfoW pidl is null!
err:shell:SHGetFileInfoW pidl is null!
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
... repeat ...
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),3,2,(nil),0,(nil)) - stub!
fixme:process:SetProcessShutdownParameters (00000100, 00000001): partial stub.
err:ntdll:NtQueryInformationToken Unhandled Token Information class 11!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),3,2,(nil),0,(nil)) - stub!
err:ole:marshal_object object doesn't expose interface {00000001-0000-0000-c000-000000000046}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:CoUnmarshalInterface Couldn't query for interface {00000001-0000-0000-c000-000000000046}, hr = 0x80004002
err:ole:CoGetClassObject no class object {663ef45e-0f11-4453-ba40-3bd14d564c71} could be created for context 0x4


So, no luck there either.

---

### Post by altonbr on 2010-03-11
This is their contact page: [https://www.citrixgcs.com/contact/g2m](https://www.citrixgcs.com/contact/g2m)

When I receive a response, I'll post it here.

---

### Post by conradin on 2010-04-22
Im dealing with this stupid Citrix thing too. How did you trick the server into thinking firefox was on OSX? Was it via the about:config useragent string? I wrote to the company, they dont offer linux support.

---

### Post by altonbr on 2010-04-22
> **conradin said:**
> Im dealing with this stupid Citrix thing too. How did you trick the server into thinking firefox was on OSX? Was it via the about:config useragent string? I wrote to the company, they dont offer linux support.

Ya it was through about:config useragent, but I used user agent switcher add-on for ease-of-use. No luck getting anything running though.

---

### Post by conradin on 2010-04-23
I think there are other strings besides the user agent that define what OS we are using. The Company evidently from the stderr i'm getting considers linux a considerable risk. Other thoughts I'm having are trying firefox under wine, or just making a virtual box thing. Those are like giving up in my mind though. I went to [www.ipswift.com](www.ipswift.com) to see just what my browser was giving up about me. even after modifying my user agent, it wasn't a significant enough change to allow any thing to run. Some time (in my infinite amounts of free time (LOLZ)) I'll have to try and figure out just what strings the g2m applications  are looking for. I have another class Tuesday, Ill see how wine treats me and post back.

what Im not sure is if the citrix app is looking for windows / mac Identifiers, or NOT windows Mac IDs. They could be looing at some other string and guessing that clients are on unsupported OSes. as usual, Im temped to buy crossover and get the technical support.

---

### Post by Afnor on 2010-07-23
Hello,

I tried also to join a gotomeeting conference, with a 9.10 installed without success.

I'd rather the firefox approach instead of my unsuccessfull IE7 one.

If i have all understood:
Basis : We need Wine as gotomeeting installs an windows .exe program.

Scenario 1 : IE 7/8/X
--> Did someone post some simple synaptic package that makes the ie install safe and well done ?

Scenario 2 : Firefox whith some hacks, like a the about:config agent name modification.
--> Does someone knows what the gdm .exe downloaded will really need
---> In [http://ubuntuforums.org/showthread.php?t=874053](http://ubuntuforums.org/showthread.php?t=874053), jrandolph seems to have succes, depending on a java installation. Does someone reproduced this succes story ?

Regards

---

### Post by brianeknoll on 2010-09-12
Yep, it's truly unfortunate that GTM doesn't support Linux. I've added my voice to the crowd suggesting they change that. This is the only "critical" that keeps me using Windows.

---

### Post by spikoley on 2010-09-23
GTM is a great app, but I wish the open source community built their own screen sharing app.

---

