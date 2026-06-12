---
title: "Google Chrome Install and Update Manager issues"
date: 2011-07-19
forum: General Help
---

### Post by charlescarroll1 on 2011-07-19
I just installed Ubuntu 11.04 on my laptop (Compaq CQ60) and I'm trying to install my preferred web browser Google Chrome. I have downloaded the .deb install file from Google twice. The file opens in Ubuntu Software Center and it shows that it is installing, but then when it reaches 100% I get an error message saying:

> [CENTER]Package Operation Failed
The installation or removal of a software package failed.[/CENTER]

Details of error message:
> InstallArchives() failed: Setting up tzdata (2011g-0ubuntu0.11.04) ...

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109.

dpkg: error processing tzdata (--configure):

 subprocess installed post-installation script returned error exit status 128

No apport report written because MaxReports is reached already
Errors were encountered while processing:

 tzdata

Setting up tzdata (2011g-0ubuntu0.11.04) ...

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109.

dpkg: error processing tzdata (--configure):

 subprocess installed post-installation script returned error exit status 128



I  don't know what the deal is but I've also been getting a similar message when I try to update the system with Update Manager. The error message is:

> [CENTER]Package operation failed

The installation or removal of a software package failed.[/CENTER]

Details of error message:
> installArchives() failed: 
Extracting templates from packages: 15%%
Extracting templates from packages: 30%%
Extracting templates from packages: 46%%
Extracting templates from packages: 61%%
Extracting templates from packages: 76%%
Extracting templates from packages: 92%%
Extracting templates from packages: 100%%

Preconfiguring packages ...


Extracting templates from packages: 15%%
Extracting templates from packages: 30%%
Extracting templates from packages: 46%%
Extracting templates from packages: 61%%
Extracting templates from packages: 76%%
Extracting templates from packages: 92%%
Extracting templates from packages: 100%%

Preconfiguring packages ...


Extracting templates from packages: 15%%
Extracting templates from packages: 30%%
Extracting templates from packages: 46%%
Extracting templates from packages: 61%%
Extracting templates from packages: 76%%
Extracting templates from packages: 92%%
Extracting templates from packages: 100%%

Preconfiguring packages ...

Setting up tzdata (2011g-0ubuntu0.11.04) ...

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109.

dpkg: error processing tzdata (--configure):

 subprocess installed post-installation script returned error exit status 128

Errors were encountered while processing:

 tzdata

Setting up tzdata (2011g-0ubuntu0.11.04) ...

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109.

dpkg: error processing tzdata (--configure):

 subprocess installed post-installation script returned error exit status 128



This is pretty sad that something like this is happening after a new install. In both cases I am not able to update or install software. Has anyone seen this issue or know how to solve it?

Thank you!

---

### Post by drpjkurian on 2011-07-19
Hi
Try running this code in terminal ```
sudo dpkg --configure -a
```

---

### Post by charlescarroll1 on 2011-07-19
That seemed to work. I was able to get Chrome installed and I'm updating now. Kind of odd how that would happen. 

Thank you much drpjkurian!

---

### Post by drpjkurian on 2011-07-19
Most welcome

---

