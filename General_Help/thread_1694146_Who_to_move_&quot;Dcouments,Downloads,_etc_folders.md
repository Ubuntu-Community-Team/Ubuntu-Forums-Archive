---
title: "Who to move &quot;Dcouments,Downloads, etc folders&quot;"
date: 2011-02-23
forum: General Help
---

### Post by DEEPfrom1 on 2011-02-23
Hey all, I am really getting the hang of Ubuntu and loving it. I have installed on my 64gb ssd. Is there a way that I can move my Music, photos, videos,downloads etc to my 500gb HDD? I know how to do this in windows. I am super lost here! If it is easier, I can re-install ubuntu 10.10 in case things must be moved during install.

Thank you much.

---

### Post by ValdeEdius on 2011-02-23
EDIT: Read your post wrong

Sounds like you are trying to change your home directory to a new path. Run this in the terminal and you should be set.
> sudo usermod -d /path/to/new/home -m

---

### Post by DEEPfrom1 on 2011-02-24
What do I do after I run that? I try typing the -d or -u in there and get nothing.

---

### Post by bluefrog on 2011-02-24
$HOME/.config/user-dirs.dirs

---

### Post by DEEPfrom1 on 2011-02-25
BLUEFROG: It says "Permission Denied"

---

### Post by bluefrog on 2011-03-02
a little short for troubleshooting.

---

### Post by grahammechanical on 2011-03-02
I would have done this differently. In fact I did do it differently.

I saved all my data and I ran the Live CD again. In my case I had to create a new partiton but in your case you have a new (another) drive. So, I suggest that you give the 64GB SSD the mount point of / and the 500GB HDD the mount point of /home. Choose a format for this drive.

You will need to reinstall Ubuntu otherwise the OS will not find the Home folder where it expects to find it. This was my mistake. It breaks the OS. Once I got over the panic, I worked out that a reinstall of the OS to the / partition would solve the problem because the OS would be told to put the Home Folder on the /home partition. It worked for me.

Regards.

---

### Post by oldos2er on 2011-03-02
It's possible to create a new /home folder without reinstalling. [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

