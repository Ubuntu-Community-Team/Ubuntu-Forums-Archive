---
title: "installation and download problems"
date: 2010-01-19
forum: General Help
---

### Post by Dreadsen on 2010-01-19
Problems installing. 

I'm brand new to linux so bare with me. 

When i try to download things or install i've been getting this

"This link needs to be opened with an application send to:" 

[http://www.getdeb.net/updates/Ubuntu/9.10/?q=minitube](http://www.getdeb.net/updates/Ubuntu/9.10/?q=minitube)

I click on "install" for this program and i get the same message.

---

### Post by dukehunter1 on 2010-01-19
Are you downloading /installing from command line?

---

### Post by Grenage on 2010-01-19
When you click on it, it asks you if you want to open the link with apturl?

---

### Post by synapsys on 2010-01-19
Have you installed the "getdeb" package like the website tells you to?

[http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)

---

### Post by Dreadsen on 2010-01-19
i thought i had getdeb already. I'll try that now.

---

### Post by Dreadsen on 2010-01-19
> **dukehunter1 said:**
> Are you downloading /installing from command line?

no.  i would like to though

---

### Post by Dreadsen on 2010-01-19
> **synapsys said:**
> Have you installed the "getdeb" package like the website tells you to?

[http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)



yes i already have getdeb installed.

---

### Post by arubislander on 2010-01-19
Is there any particular software that you think you need to get from GetDeb that's not in the repositories?

As you mention being new to Linux, maybe you should stick to installing from the repositories at first.

---

### Post by Dreadsen on 2010-01-19
> **arubislander said:**
> Is there any particular software that you think you need to get from GetDeb that's not in the repositories?

As you mention being new to Linux, maybe you should stick to installing from the repositories at first.


yeah i want minitube so i can watch youtube videos with out any problems.  I am brand spanking new you linux and i have NO windows on my machine at all.  So i went cold turkey on windows.  
On my spare time i watch news programs on youtube. In between learning how to navigate and operate on linux i just want to get a few things done. I have problems watching other flash videos even with the update install and i've tried following the directions in a couple of other links which others claim to have resolved the issue but being that i'm a super noob it didn't work. 

So i'll look into learning how to install from the repositories.

---

### Post by arubislander on 2010-01-19
Ok... minitube is not in the regular repositories... so you're right on track gettingit from [www.getdeb.net](www.getdeb.net)

---

### Post by synapsys on 2010-01-19
Try this:

[QUOTE=www.getdeb.net]

***Go to System-Administration-Software Sources, Third-Party Software tab, Add:***```
deb http://archive.getdeb.net/ubuntu karmic-getdeb apps
```**Add the repository GPG key, open a terminal window and type:**
                                 ```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```[/QUOTE]

Also make sure you have apturl installed:

```
aptitude search apturl
```
Should have an "i" in front of it for "installed"

---

