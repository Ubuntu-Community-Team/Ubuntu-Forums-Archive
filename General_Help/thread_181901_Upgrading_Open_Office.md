---
title: "Upgrading Open Office"
date: 2006-05-25
forum: General Help
---

### Post by cobbweb on 2006-05-25
I was wondering how I could upgrade open office from 2.0 to 2.0.2  I tried 

 sudo apt-get install openoffice 

 but it says 

Open Office is not avalible but is refered to by another package. This may mean the package is missing or obsolete or only avalible from another source. 


 where or what do i do now???? Any Help is well needed thank you ,,, 

 Cobbweb

---

### Post by cskeide on 2006-05-25
This might help.
```
apt-cache search openoffice.org
```

I think the packagename is openoffice.org2, so this would install it:
```
sudo apt-get install openoffice.org2
```

However, if you have already installed openoffice and you are running Breezy, this command will not upgrade to the 2.0.2 version. On the other hand, if you have added some extra repositories for openoffice2 this would upgrade to the newest available version:
```
sudo apt-get update && sudo apt-get upgrade
```

The Dapper Drake release includes the newest openoffice packages, and the release date for dapper is 1st of June.

Hope this helps.

---

### Post by cobbweb on 2006-05-25
Wow, Dapper is coming out June 1? Will I have to delete my OS to add the new one on? or is there a way to keep everything I all ready have and still upgrade... 


 Cobbweb

---

### Post by cskeide on 2006-05-25
[QUOTE=cobbweb]Wow, Dapper is coming out June 1? Will I have to delete my OS to add the new one on? or is there a way to keep everything I all ready have and still upgrade...[/QUOTE]

You will be able to keep your existing install and upgrade with apt. Instructions for upgrading will most likely be included in the release notes for dapper, but it should be as easy as editing your /etc/apt/sources.list and running:```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by Ted_Smith on 2006-06-05
sudo gedit /etc/apt/sources.list

Then I add this line:

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

Save & close the file, & then run the following commands:

sudo apt-get update

sudo apt-get upgrade

Source : [http://lxer.com/module/newswire/view/53395/index.html](http://lxer.com/module/newswire/view/53395/index.html)

---

