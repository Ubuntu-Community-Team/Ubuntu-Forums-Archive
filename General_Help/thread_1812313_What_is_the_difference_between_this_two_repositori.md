---
title: "What is the difference between this two repositories?"
date: 2011-07-26
forum: General Help
---

### Post by a.toraby on 2011-07-26
I wanted to install sun jdk today. I surfed the Internet and I found that I should add one of this repositories:

[LIST]
[*]deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
[*]ppa:ferramroberto/java
[/LIST]
What is the difference between this two repositories?
I know that deb mentions that this is a deb package, But What's the meaning of ppa?
Could you explain me, How can I download files from this repositories and install them off line?

---

### Post by ajgreeny on 2011-07-26
I have absolutely no idea about the second of those two repositories, but I can see no real reason forusing it as it does not appear to have a newer version of java than the canonical archive.

Why do you need to download in install offline?  If you want to use the ppa go to [https://launchpad.net/~ferramroberto/+archive/java](https://launchpad.net/~ferramroberto/+archive/java) and read the "Adding this ppa to your system" then it will appear like any other repository.

---

### Post by Theredbaron1834 on 2011-07-26
Yeah, I don't have any idea what would have a newer one. But, if you add the repo, apt-get will just pick the newest one, so not much reason not to if you want too.


As for downloading offline, that is easy. The best way I know, so that it grabs all the deps too, is to open up synaptic, click the proggies you want, and then click "file" and then "Generate Package Download Script". This lets you make a script that, as it says, downloads all the packages. Once it is saved, run it. It will wget all the packages to the same dir that the script is in. 

Once done, you can move the packages to another comp, or whatever. Then open up synaptic again and go to "file" and "Add Downloaded Packages" and point the browser to the package folder. 

There are other ways too, like apt-get -d, copy the temp files, then dpkg. But I think this is the easiest way. This, or apt-offline, is how I update my ofline comp's.

---

### Post by a.toraby on 2011-12-13
Thanks for your great solution. I've tried synaptic in that way and now I can move sources to different computers successfully.
But I'd prefer to use command line to do this. when I try "apt-get -d" it doesn't download dependencies. for example when I try to get flashplugin. It only downloads flashplugin-installer_11.1.102.55ubuntu0.11.10.1_amd64. I've tried several options like -f but there wasn't any good result. can you help me in this regard?

---

