---
title: "Copy command errors"
date: 2012-03-11
forum: General Help
---

### Post by Robert R on 2012-03-11
[Hi,]("http://ubuntuforums.org/member.php?u=1145020")
    Trying to copy the virtual box guest additions packages to the [COLOR=Red]/usr/share/virtualbox[/COLOR] using the following command. 

root@colene-desktop:/home/colene# sudo cp -f /home/colene/Downloads/vb /usr/share/virtualbox 

however i keep getting the following errors

[COLOR=Red]cp: omitting directory `/home/colene/Downloads/vb'[/COLOR]

Someone plese explain and indicate how the files can be copied

---

### Post by MG&amp;TL on 2012-03-11
If you are copying directories,* cp  *needs the -r option.

In your case:

```
sudo cp -rf /home/colene/Downloads/vb /usr/share/virtualbox 
```Although "sudo" as root isn't necessary. Just login as per normal, then use sudo. That's the point: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I'm thinking you want to place things in the /usr/share/virtualbox/ folder though, not replace it. In which case, use:

```
sudo cp -rf /home/colene/Downloads/vb /usr/share/virtualbox/
```

---

### Post by matt_symes on 2012-03-11
Hi

You need to specify what to copy. To copy everything in that directory use the * glob

```
sudo cp /home/colene/Downloads/vb/* /usr/share/virtualbox
```

To copy everything in the directory and sub directories use the -r switch.

```
sudo cp -r /home/colene/Downloads/vb/* /usr/share/virtualbox
```

To copy a singe file

```
sudo cp /home/colene/Downloads/vb/<name_of_file> /usr/share/virtualbox
```

You can do other copying operations as well using wildcards.

EDIT: Any reason you were using the -f switch ?

Kind regards

---

