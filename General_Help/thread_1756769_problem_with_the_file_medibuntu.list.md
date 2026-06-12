---
title: "problem with the file medibuntu.list"
date: 2011-05-12
forum: General Help
---

### Post by mospel on 2011-05-12
greetings 
I have this problem: when I launch synaptic or when I try to update any repository I have this error message: 
 ```
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```I tried to fix it by following this procedure:

```

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.bad
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```However when I write the last instruction the next message appear: 
```
N: Ignoring file 'medibuntu.list.bad' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
```Someone knows how to fix this error? I have tried it a lot of times and always happens the same thing

best regards

---

### Post by plucky on 2011-05-12
Go [Here](https://help.ubuntu.com/community/Medibuntu) and use the command specified to install the medibuntu repository.

Also delete the medibuntu.list.bad file first.

If that doesn't work,post the actual contents of the medibuntu.list file.

Good Luck

---

### Post by mospel on 2011-05-12
I did this:
```
milton@mirp-workstation:/$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2011-05-11 17:17:48--  http://www.medibuntu.org/sources.list.d/natty.list
Resolving www.medibuntu.org... 88.191.127.22
Connecting to www.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 302 Moved
Location: http://10.0.16.15:15871/cgi-bin/blockpage.cgi?ws-session=1998876452 [following]
--2011-05-11 17:17:54--  http://10.0.16.15:15871/cgi-bin/blockpage.cgi?ws-session=1998876452
Connecting to 10.0.16.15:15871... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1505 (1.5K) [text/html]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[=============================================================================================================================================================>] 1,505       --.-K/s   in 0s      

2011-05-11 17:17:54 (203 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [1505/1505]

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
```this is the actual content of the file:
```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">

<!--//////////////////////////////////////////////////////////////////////////
//
//    Copyright (c) 1996 - 2009, Websense, Inc.    All Rights Reserved
//    See WebsenseCopyright.txt for copyright information
//
///////////////////////////////////////////////////////////////////////////-->

<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Access to this site is blocked</title>
</head>
<body>

<!--[if lt IE 7]> <div style="width: 725px;"> <![endif]-->
<div style="border: 1px solid #285EA6;width: 95%; max-width: 700px; overflow: hidden; margin-left: 10px; background-color: #EEF2F7;">
    <iframe src="http://10.0.16.15:15871/cgi-bin/block_message.cgi?ws-session=1998876452" title="test" name="ws_block" frameborder="0" scrolling="auto" style="width:100%; height: 10em;">

    </iframe>
    <iframe src="http://10.0.16.15:15871/cgi-bin/blockOptions.cgi?ws-session=1998876452" name="ws_blockoption" frameborder="0" scrolling="auto" style="width:100%; height: 17.5em;">
        <p>To enable further options, view this page with a browser that supports iframes</p>
    </iframe>
    <div><img title="Websense" src="/Images/wslogo_block_page.png" alt="Websense Logo" style="float: right;clear: both;margin: 0px 10px 6px 0px; padding: 2px 0px;">
        <div style="clear: both; overflow: hidden; height:1px;"></div>
    </div>
</div>
<!--[if lt IE 7]> </div> <![endif]-->

</body>
</html>
```

---

### Post by oldos2er on 2011-05-12
medibuntu.list should look like this:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free

---

### Post by plucky on 2011-05-13
Something doesn't look right.
> --2011-05-11 17:17:48--  [http://www.medibuntu.org/sources.list.d/natty.list](http://www.medibuntu.org/sources.list.d/natty.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 88.191.127.22
Connecting to [www.medibuntu.org|88.191.127.22|:80](www.medibuntu.org|88.191.127.22|:80)... connected.
[color=red]HTTP request sent, awaiting response... 302 Moved
Location: [http://10.0.16.15:15871/cgi-bin/blockpage.cgi?ws-session=1998876452](http://10.0.16.15:15871/cgi-bin/blockpage.cgi?ws-session=1998876452) [following]
--2011-05-11 17:17:54--  [http://10.0.16.15:15871/cgi-bin/blockpage.cgi?ws-session=1998876452](http://10.0.16.15:15871/cgi-bin/blockpage.cgi?ws-session=1998876452)
Connecting to 10.0.16.15:15871... connected.[/color]
HTTP request sent, awaiting response... 200 OK
Length: 1505 (1.5K) [text/html]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

Your wget is being re-directed

This is what I get when I run that command ```
--2011-05-13 08:25:22--  http://www.medibuntu.org/sources.list.d/natty.list
Resolving www.medibuntu.org... 88.191.127.22
Connecting to www.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 274 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[===================================================================================>] 274         --.-K/s   in 0s      

2011-05-13 08:25:22 (3.33 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [274/274]

Ign http://archive.canonical.com natty InRelease
Hit http://packages.medibuntu.org natty InRelease
Ign http://extras.ubuntu.com natty InRelease
Ign http://gb.archive.ubuntu.com natty InRelease
Ign http://gb.archive.ubuntu.com natty-updates InRelease
Ign http://gb.archive.ubuntu.com natty-security InRelease
Hit http://gb.archive.ubuntu.com natty Release.gpg
Get:1 http://archive.canonical.com natty Release.gpg [198 B]
Get:2 http://extras.ubuntu.com natty Release.gpg [72 B]
Hit http://gb.archive.ubuntu.com natty-updates Release.gpg
Hit http://extras.ubuntu.com natty Release
Get:3 http://archive.canonical.com natty Release [5,916 B]
Hit http://gb.archive.ubuntu.com natty-security Release.gpg
Hit http://gb.archive.ubuntu.com natty Release
Hit http://extras.ubuntu.com natty/main i386 Packages
Hit http://packages.medibuntu.org natty/free i386 Packages
Hit http://gb.archive.ubuntu.com natty-updates Release
Get:4 http://archive.canonical.com natty/partner i386 Packages [7,871 B]
Ign http://extras.ubuntu.com natty/main TranslationIndex
Hit http://gb.archive.ubuntu.com natty-security Release
Hit http://gb.archive.ubuntu.com natty/main i386 Packages
Hit http://gb.archive.ubuntu.com natty/restricted i386 Packages
Hit http://gb.archive.ubuntu.com natty/universe i386 Packages
Hit http://gb.archive.ubuntu.com natty/multiverse i386 Packages
Hit http://packages.medibuntu.org natty/non-free i386 Packages
Ign http://gb.archive.ubuntu.com natty/main TranslationIndex
Ign http://gb.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://gb.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://gb.archive.ubuntu.com natty/universe TranslationIndex
Ign http://archive.canonical.com natty/partner TranslationIndex
Hit http://gb.archive.ubuntu.com natty-updates/main i386 Packages
Hit http://gb.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://gb.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://packages.medibuntu.org natty/free TranslationIndex
Ign http://gb.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://gb.archive.ubuntu.com natty-updates/universe TranslationIndex
Hit http://gb.archive.ubuntu.com natty-security/main i386 Packages
Hit http://gb.archive.ubuntu.com natty-security/restricted i386 Packages
Hit http://gb.archive.ubuntu.com natty-security/universe i386 Packages
Hit http://gb.archive.ubuntu.com natty-security/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com natty-security/main TranslationIndex
Ign http://gb.archive.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://gb.archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://gb.archive.ubuntu.com natty-security/universe TranslationIndex
Ign http://packages.medibuntu.org natty/non-free TranslationIndex
Hit http://gb.archive.ubuntu.com natty/main Translation-en_GB
Hit http://gb.archive.ubuntu.com natty/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com natty/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com natty/universe Translation-en_GB
Ign http://extras.ubuntu.com natty/main Translation-en_GB
Ign http://extras.ubuntu.com natty/main Translation-en
Ign http://archive.canonical.com natty/partner Translation-en_GB
Ign http://archive.canonical.com natty/partner Translation-en
Ign http://gb.archive.ubuntu.com natty/main Translation-en
Ign http://gb.archive.ubuntu.com natty/multiverse Translation-en
Ign http://gb.archive.ubuntu.com natty/restricted Translation-en
Ign http://gb.archive.ubuntu.com natty/universe Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/main Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com natty-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-security/main Translation-en
Ign http://gb.archive.ubuntu.com natty-security/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://gb.archive.ubuntu.com natty-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-security/restricted Translation-en
Ign http://gb.archive.ubuntu.com natty-security/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-security/universe Translation-en
Ign http://packages.medibuntu.org natty/free Translation-en_GB
Ign http://packages.medibuntu.org natty/free Translation-en
Ign http://packages.medibuntu.org natty/non-free Translation-en_GB
Ign http://packages.medibuntu.org natty/non-free Translation-en
Fetched 14.1 kB in 4s (2,860 B/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Ign http://extras.ubuntu.com natty InRelease
Ign http://archive.canonical.com natty InRelease
Ign http://gb.archive.ubuntu.com natty InRelease
Ign http://gb.archive.ubuntu.com natty-updates InRelease
Ign http://gb.archive.ubuntu.com natty-security InRelease
Hit http://packages.medibuntu.org natty InRelease
Hit http://archive.canonical.com natty Release.gpg
Hit http://extras.ubuntu.com natty Release.gpg
Hit http://gb.archive.ubuntu.com natty Release.gpg
Hit http://archive.canonical.com natty Release
Hit http://extras.ubuntu.com natty Release
Hit http://gb.archive.ubuntu.com natty-updates Release.gpg
Hit http://gb.archive.ubuntu.com natty-security Release.gpg
Hit http://gb.archive.ubuntu.com natty Release
Hit http://gb.archive.ubuntu.com natty-updates Release
Hit http://packages.medibuntu.org natty/free i386 Packages
Hit http://gb.archive.ubuntu.com natty-security Release
Hit http://archive.canonical.com natty/partner i386 Packages
Ign http://archive.canonical.com natty/partner TranslationIndex
Hit http://packages.medibuntu.org natty/non-free i386 Packages
Hit http://extras.ubuntu.com natty/main i386 Packages
Hit http://gb.archive.ubuntu.com natty/main i386 Packages
Ign http://extras.ubuntu.com natty/main TranslationIndex
Ign http://packages.medibuntu.org natty/free TranslationIndex
Hit http://gb.archive.ubuntu.com natty/restricted i386 Packages
Hit http://gb.archive.ubuntu.com natty/universe i386 Packages
Hit http://gb.archive.ubuntu.com natty/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com natty/main TranslationIndex
Ign http://gb.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://gb.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://gb.archive.ubuntu.com natty/universe TranslationIndex
Hit http://gb.archive.ubuntu.com natty-updates/main i386 Packages
Hit http://gb.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://gb.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://gb.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://gb.archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://packages.medibuntu.org natty/non-free TranslationIndex
Hit http://gb.archive.ubuntu.com natty-security/main i386 Packages
Hit http://gb.archive.ubuntu.com natty-security/restricted i386 Packages
Hit http://gb.archive.ubuntu.com natty-security/universe i386 Packages
Hit http://gb.archive.ubuntu.com natty-security/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com natty-security/main TranslationIndex
Ign http://gb.archive.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://gb.archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://gb.archive.ubuntu.com natty-security/universe TranslationIndex
Hit http://gb.archive.ubuntu.com natty/main Translation-en_GB
Hit http://gb.archive.ubuntu.com natty/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com natty/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com natty/universe Translation-en_GB
Ign http://archive.canonical.com natty/partner Translation-en_GB
Ign http://archive.canonical.com natty/partner Translation-en
Ign http://extras.ubuntu.com natty/main Translation-en_GB
Ign http://extras.ubuntu.com natty/main Translation-en
Ign http://gb.archive.ubuntu.com natty/main Translation-en
Ign http://gb.archive.ubuntu.com natty/multiverse Translation-en
Ign http://gb.archive.ubuntu.com natty/restricted Translation-en
Ign http://gb.archive.ubuntu.com natty/universe Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/main Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com natty-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com natty-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-security/main Translation-en
Ign http://gb.archive.ubuntu.com natty-security/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://gb.archive.ubuntu.com natty-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-security/restricted Translation-en
Ign http://gb.archive.ubuntu.com natty-security/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com natty-security/universe Translation-en
Ign http://packages.medibuntu.org natty/free Translation-en_GB
Ign http://packages.medibuntu.org natty/free Translation-en
Ign http://packages.medibuntu.org natty/non-free Translation-en_GB
Ign http://packages.medibuntu.org natty/non-free Translation-en
Reading package lists...

```

What is **[http://10.0.16.15:15871/](http://10.0.16.15:15871/)** as that address I think is on your network.You are being blocked from using wget on the internet.

Good Luck

---

