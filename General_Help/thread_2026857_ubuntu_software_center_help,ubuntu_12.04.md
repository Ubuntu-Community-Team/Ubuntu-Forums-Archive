---
title: "ubuntu software center help,ubuntu 12.04"
date: 2012-07-15
forum: General Help
---

### Post by yellowwinner on 2012-07-15
hello everyone,

I'm having trouble with the software center,when every I click install and I type my password the install bar appears and disappears and then it says the install button again and no install bar.

Then, I open termal and type

sudo apt-install Openshot

and it says 


```
sudo apt-get install Openshot
[sudo] password for *****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package Openshot
```

Then i try it with out
caps and openshot videio editor

none of them worked.

Just to let You know I have ubuntu 12.04 64X

please help,yellowwinner

---

### Post by robtygart on 2012-07-15
Try this first.   
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by papibe on 2012-07-15
> **yellowwinner said:**
> sudo apt-install Openshot

Hi yellowwinner.

Most of the packages are named in lower case, and that is the case of Openshot too.

Try this:
```
 sudo apt-get install openshot
```

You can use apt-cache to search for actual package names:
```
$ apt-cache search Openshot
**openshot** - Create and edit videos and movies
openshot-doc - Help manual for OpenShot Video Editor
```
I hope that helps, and let us know how it goes.
Regards.

---

### Post by yellowwinner on 2012-07-15
> **robtygart said:**
> Try this first.   
```
sudo apt-get update
sudo apt-get upgrade
```

thank you robtygart it worked:)

> **papibe said:**
> Hi yellowwinner.

Most of the packages are named in lower case, and that is the case of Openshot too.

Try this:
Code:
 sudo apt-get install openshot
You can use apt-cache to search for actual package names:
Code:
$ apt-cache search Openshot
openshot - Create and edit videos and movies
openshot-doc - Help manual for OpenShot Video Editor
I hope that helps, and let us know how it goes.
Regards.

Thanks for telling me this next time I have that problem i9ll try this way and post a reply on what happened.

---

### Post by robtygart on 2012-07-15
Cool!!! I am glad it worked. :-D.

---

### Post by robtygart on 2012-07-16
> **papibe said:**
> 

You can use apt-cache to search for actual package names:
```
$ apt-cache search Openshot
**openshot** - Create and edit videos and movies
openshot-doc - Help manual for OpenShot Video Editor
```

Thank you for the new command, this will come in handy.

---

