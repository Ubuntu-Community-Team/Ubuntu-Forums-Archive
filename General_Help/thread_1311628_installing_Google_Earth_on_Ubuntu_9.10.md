---
title: "installing Google Earth on Ubuntu 9.10"
date: 2009-11-02
forum: General Help
---

### Post by jhb1608 on 2009-11-02
oh I didn't know they already made Google Earth in Linux? Do there is a 32-bit version?

---

### Post by chriskin on 2009-11-02
> **jhb1608 said:**
> oh I didn't know they already made Google Earth in Linux? Do there is a 32-bit version?

there most probably are both 32bit and 64bit version. 
i'm not sure for 32 as i don't have a 32bit installation, but there has to be

the 64bit one works just fine by the way
faster than the windows version for sure

---

### Post by jhb1608 on 2009-11-02
Well should I Google for it? I'll let ya know.

Hm... interesting, it is only in .bin, not tar.gz or other familiar format. I don't know how to install the .bin. So I will rather have a familiar format so it is easily installable.

---

### Post by chriskin on 2009-11-02
> **jhb1608 said:**
> Well should I Google for it? I'll let ya know.

Hm... interesting, it is only in .bin, not tar.gz or other familiar format. I don't know how to install the .bin. So I will rather have a familiar format so it is easily installable.

i say once more that there is a repository that you can add through ubuntu tweak with a single click or any other way you like and then you can install google earth via the package manager, once again with a single click And have it autoupdate if a new version comes

---

### Post by jhb1608 on 2009-11-02
> **chriskin said:**
> i say once more that there is a repository that you can add through ubuntu tweak with a single click or any other way you like and then you can install google earth via the package manager, once again with a single click And have it autoupdate if a new version comes

How do you tweak it via the repository, then?

---

### Post by chriskin on 2009-11-02
> **jhb1608 said:**
> How do you tweak it via the repository, then?

i can't understand what you are asking...

---

### Post by jhb1608 on 2009-11-02
> **chriskin said:**
> i say once more that there is a repository that you can add through ubuntu tweak with a single click or any other way you like and then you can install google earth via the package manager, once again with a single click And have it autoupdate if a new version comes

you say that in the above message. How do I add the Googleearthlinux.bin repository in Ubuntu?

---

### Post by xtremesupremacy3 on 2009-11-02
As Chriskin has already correctly pointed out, it is available in the medibuntu repositories.
To add the repositories, follow the instructions on their website and after that you can use Synaptic.

If you are certain you wish to use the bin file, then do as followed:

After having downloaded the file (in this example I use fileName.bin downloaded to the desktop):

```
cd Desktop
```
After that type the following to make it executable (make sure you check for uppercases as it's case sensitive:
```
sudo chmod +x fileName.bin
```
Then in order to execute it, simply run:
```
sudo ./fileName.bin
```

---

### Post by chriskin on 2009-11-02
> **jhb1608 said:**
> you say that in the above message. How do I add the Googleearthlinux.bin repository in Ubuntu?

via the "ubuntu tweak" application would be a good way
i don't know the link to the repository itself

seems it's on medibuntu, search for medibuntu on google then :) it's even easier to install that way

---

### Post by jhb1608 on 2009-11-02
> **xtremesupremacy3 said:**
> As Chriskin has already correctly pointed out, it is available in the medibuntu repositories.
To add the repositories, follow the instructions on their website and after that you can use Synaptic.

If you are certain you wish to use the bin file, then do as followed:

After having downloaded the file (in this example I use fileName.bin downloaded to the desktop):

```
cd Desktop
```
After that type the following to make it executable (make sure you check for uppercases as it's case sensitive:
```
sudo chmod +x fileName.bin
```
Then in order to execute it, simply run:
```
sudo ./fileName.bin
```

Oh Nevermind it works! Thanks.

I'm not in Mediubuntu, sir. I'm **on Ubuntu Karmic Koala 9.10.** Thanks.

A bit sluggish, hm.

---

### Post by chriskin on 2009-11-02
> **jhb1608 said:**
> I'm not in Mediubuntu, sir. I'm **on Ubuntu Karmic Koala 9.10.** Thanks.

medibuntu is Not a release of ubuntu :popcorn:

it's a repisitory of applications :P

---

### Post by aysiu on 2009-11-02
64-bit is definitely available through the Medibuntu repositories:
[http://packages.medibuntu.org/jaunty/googleearth.html](http://packages.medibuntu.org/jaunty/googleearth.html)

If you don't know how to add the Medibuntu repositories, this will help you:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

If you don't know what repositories are, this will help you:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by jhb1608 on 2009-11-02
Note: It do work in 32-bit Karmic Koala Ubuntu also!

But problem is: I need a better video card so Google Earth will be a lot faster.

---

### Post by jhb1608 on 2009-11-02
Hm... One issue I face on the Google Earth Linux is:

The desktop icon won't open and says:

"Could not display "/home/jason/Desktop/Google-googleearth.desktop". The location is not a folder."

Odd.
Also, faced the other error:

"Could not create directory: /root/.googleearth"

"Could not create directory: /root/.googleearth/Cache"

Google Earth could not write to the current cache or myplaces file location. The values will be set as follows: 
My Places Path: "/home/jason/.googleearth"
Cache Path: "/home/jason/.googleearth/Cache" 

But after I click OK 3 times and it loads Google Earth Linux just fine, odd.

---

### Post by jhb1608 on 2009-11-02
Anyone know how to fix this bug?

---

### Post by blur xc on 2009-11-02
> **jhb1608 said:**
> Anyone know how to fix this bug?

Yes...  Yes I do.  I had the same problem in 9.04.  There's a config (.googleearthconfig??) file that has the wrong paths in it, you have to edit it to make it look into your home directory, not root.

Let me see if I can find the details...

hang on...

BM

edit-  found it- [http://ubuntuforums.org/showpost.php?p=7501478&postcount=6](http://ubuntuforums.org/showpost.php?p=7501478&postcount=6)

---

### Post by jhb1608 on 2009-11-02
Thanks :). Oh wait, I don't find .conf folder... where is it? And how do I do those commands? I know it is done by terminal, but I'm not sure. You'd need to provide the specific directions, so I know what to do.

I can't do anything until you explain the tutorial a bit more clear and I can follow the steps.

---

### Post by jhb1608 on 2009-11-02
Well?

---

### Post by 565Customz on 2009-11-02
the config file might be hidden, go to edit>preferences (i think) and click show hidden files and folders...when you find it, right click and open as administrator. 

you can also open it from the terminal, but since i dont know your exact file path, im not gonna bother with it

---

### Post by jhb1608 on 2009-11-02
Fixed! :).

---

### Post by jhb1608 on 2009-11-02
> **565Customz said:**
> the config file might be hidden, go to edit>preferences (i think) and click show hidden files and folders...when you find it, right click and open as administrator. 

you can also open it from the terminal, but since i dont know your exact file path, im not gonna bother with it

Solved by your method, it works.

---

### Post by blur xc on 2009-11-02
> **565Customz said:**
> the config file might be hidden, go to edit>preferences (i think) and click show hidden files and folders...when you find it, right click and open as administrator. 

you can also open it from the terminal, but since i dont know your exact file path, im not gonna bother with it


Sorry- I guess I'm propagating my original complaint about incomplete instructions that assume the user has some level of linux knowledge...

"ctrl-h" in nautilus to show hidden folders.

Those are commands to run in the terminal - applications -> accessories -> terminal

And no, you do not need to edit those files as administrator.  All files in your home folder are owned by you, and do not need root access to modify them.

Glad it worked for you.  I love google earth, one of my favorite apps to play with.  All they need to do to make it better is to put street view in it, as well as the "get directions" functionality you get on google maps (ie. drag blue line, etc...).

BM

---

