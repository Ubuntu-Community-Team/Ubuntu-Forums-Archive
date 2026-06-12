---
title: "Installing from not authenticated sources"
date: 2011-11-19
forum: General Help
---

### Post by Tornikee on 2011-11-19
I opened a thread about this some days ago in the Installations section, but would like more hints, so thought I'd post here too.

This is what I wrote in that topic:

> Some days ago I tried to install Firefox, but got stuck at the 'requires installation of untrusted packages' error, until members of this forum [hinted]("http://ubuntuforums.org/showthread.php?p=11446322#post11446322") how to bypass the Software Center installation via terminal.

That was all fine, but I get the same error w/ other applications. Minutes ago I tried installing the indicator-sysmonitor 0.3.9 app via the .deb file (like the initial Firefox installation I tried) and got to the same message.

Since then, this issue has extended to regular (Banshee, etc) updates like this: [https://lh3.googleusercontent.com/-RnqT5hsYM7g/Tse34Zo2mBI/AAAAAAAADPc/Dk0Nj99-dY8/s0/Screenshot%252520at%2525202011-11-19%25252018%25253A05%25253A33.png](https://lh3.googleusercontent.com/-RnqT5hsYM7g/Tse34Zo2mBI/AAAAAAAADPc/Dk0Nj99-dY8/s0/Screenshot%252520at%2525202011-11-19%25252018%25253A05%25253A33.png)

So can I do anything about this error message? I went over options in software sources etc. but nothing has changed, so seems like I need to change something in other way.

---

### Post by Bobhuber on 2011-11-19
> **Tornikee said:**
> I opened a thread about this some days ago in the Installations section, but would like more hints, so thought I'd post here too.

This is what I wrote in that topic:



Since then, this issue has extended to regular (Banshee, etc) updates like this: [https://lh3.googleusercontent.com/-RnqT5hsYM7g/Tse34Zo2mBI/AAAAAAAADPc/Dk0Nj99-dY8/s0/Screenshot%252520at%2525202011-11-19%25252018%25253A05%25253A33.png](https://lh3.googleusercontent.com/-RnqT5hsYM7g/Tse34Zo2mBI/AAAAAAAADPc/Dk0Nj99-dY8/s0/Screenshot%252520at%2525202011-11-19%25252018%25253A05%25253A33.png)

So can I do anything about this error message? I went over options in software sources etc. but nothing has changed, so seems like I need to change something in other way.
First install the synaptic package manager - configure your PPAS and preferences thru that  and use that for package installation. Second install  gdebi which is a tool to install .deb files. Once installed it will be an option when you right click on a .deb file and should get rid of a lot of your problems. Just be sure you know that your source files are indeed from trusted sources.

---

### Post by Tornikee on 2011-11-19
Thanks a lot for the information.

---

### Post by Tornikee on 2011-11-19
Could you please hint how I should install packages via Synaptic, and which preferences I should check there in regard to untrusted packages? Cause I can't find anything that would change this issue.
And installing gdeb via Software Center causes the same 'requires installation of untrusted packages' error: [https://lh3.googleusercontent.com/-03rLl23h9Zs/TsgVTcx1AGI/AAAAAAAADP0/2IXpslvWpDc/s0/Screenshot%252520at%2525202011-11-20%25252000%25253A42%25253A06.png](https://lh3.googleusercontent.com/-03rLl23h9Zs/TsgVTcx1AGI/AAAAAAAADP0/2IXpslvWpDc/s0/Screenshot%252520at%2525202011-11-20%25252000%25253A42%25253A06.png)

---

### Post by Bobhuber on 2011-11-19
> **Tornikee said:**
> Could you please hint how I should install packages via Synaptic, and which preferences I should check there in regard to untrusted packages? Cause I can't find anything that would change this issue.
And installing gdeb via Software Center causes the same 'requires installation of untrusted packages' error: [https://lh3.googleusercontent.com/-03rLl23h9Zs/TsgVTcx1AGI/AAAAAAAADP0/2IXpslvWpDc/s0/Screenshot%252520at%2525202011-11-20%25252000%25253A42%25253A06.png]("https://lh3.googleusercontent.com/-03rLl23h9Zs/TsgVTcx1AGI/AAAAAAAADP0/2IXpslvWpDc/s0/Screenshot%252520at%2525202011-11-20%25252000%25253A42%25253A06.png")
The whole idea of installing the synaptic package manager is to use it to install software INSTEAD of the Software Center which has problems.Assuming you have synaptic installed just type the first few letters (or the name) of the package you want to install into the Quick Filter bar in synaptic and it will show up in the list of available packages.
You may also have a currupted package list. In that case this should fix it. From a terminal >
sudo rm -r /var/lib/apt/lists
 sudo mkdir -p /var/lib/apt/lists/partial
 sudo aptitude update

---

### Post by Tornikee on 2011-11-19
Thanks for reply. I managet to install some packages from Synaptic and also the update packages' issue hasn't appeared when I ran updates.

Thanks again.

---

### Post by Bobhuber on 2011-11-19
> **Tornikee said:**
> Thanks for reply. I managet to install some packages from Synaptic and also the update packages' issue hasn't appeared when I ran updates.

Thanks again.
Your welcome. Mark this thread as solved so it might help someone else.

---

