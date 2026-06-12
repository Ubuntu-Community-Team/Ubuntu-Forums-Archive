---
title: "I have no permissions on the partition I just created"
date: 2010-06-27
forum: General Help
---

### Post by fiberain on 2010-06-27
Hi,
I am a new user of Ubuntu, I wanted to give it some space, so I created a 500GB primary partition on the hard disk using  GParted. I formatted it with ext2 file system. It is called /dev/sda3. Just a place to put media files. I was able to mount the volume using Ubuntu's disk utility. But when I tried to create a folder on it, I  found that I was not the owner of the drive, *root* was, and therefore no-go.I know this is a very new-be question, but how do I get  permission to use my new partition?
Thanking you,
fiberain:guitar:

---

### Post by Sonsum on 2010-06-27
I don't know the exact settings to solve this, but what I generally do is look at the permissions of a file I can edit, and copy those settings into the newly created directory.

---

### Post by Sonsum on 2010-06-27
You can find these by right clicking on a directory and clicking properties. There should be a permissions tab.

---

### Post by MooPi on 2010-06-27
Did you name the new drive partition ? I would name the drive in gparted then  create a drive in /media by the same name,edit fstab to have that drive mount on /media/yourdrivesname. Let me know if you need assistance past this. Make certain you own the new /media location.

---

### Post by gadolinio on 2010-06-28
The folder's owner is root, and that's ok. What you need is that the folder has all permissions set for every user, even if not the owner.
Open the partition with the file navigator like you normally do to see files in  it. Then go up one level (press the backspace key once); you should be in the <media> folder, and the folder you've just left should be highlighted. It can be something like sda3, or the partition's label. Suppose it's sda3.
Now, open a terminal (applications--> accesiories--> terminal). In this case you would type:
```

cd /media

```Then:
```

sudo chmod a=rwx -R sda3

```After you hit enter, you'll be asked for your password. Enter it, although you won't see it in the screen, not even like "*****". The terminal is still taking your input; you just type your pwd and press enter.
That's it.

---

### Post by gadolinio on 2010-06-28
For you to know what you're doing:

cd /media: positions you in the folder containing <<the folder where your partition is mounted>> (UNIX stuff... You can read about that if you're interested). So the next command will be applied to elements inside /media, like sda3.

sudo: this allows you to gain special privileges in order to perform this task, which your user normally can't. For that, you're asked for your password.

chmod: this is the command "itself". It is used to change permissions on files and directories.

a=rwx: this means you're setting permission for all users (a), to read (r), write (w), and execute (x).

-R: means that the command applies to all subfolders and files inside them.

sda3: obviously, this is the element inside /media for which the permissions are being set.

---

### Post by fiberain on 2010-06-28
To all who replied with your helpful suggestions:
Thanks so much for making me feel welcome in this community. Gadolinio, your suggestion was right on the money. It took 30 seconds, and I was able to use my new partition. I hope that someday I can be as helpful as you all were!

Sincerely,
Fiberain:guitar::grin::grin::grin::grin::grin:

---

### Post by gadolinio on 2010-06-28
> **fiberain said:**
> To all who replied with your helpful suggestions:
Thanks so much for making me feel welcome in this community. Gadolinio, your suggestion was right on the money. It took 30 seconds, and I was able to use my new partition. I hope that someday I can be as helpful as you all were!

Sincerely,
Fiberain:guitar::grin::grin::grin::grin::grin:

You're welcome. Feel free to ask for help here whenever you need to. If you continue using the system, and reading about it, maybe even experimenting a little (at your own risk! :P ), etc, you'll probably be able to help others in some time. You can visit the forums even if you don't have a question, to see what problems happen more often and how they're solved. Good luck ubuntu-ing!

---

### Post by quirkification on 2010-06-28
Good timing, i just re installed to move ubuntu to the beginning of the drive for faster writing. Once I found another 85GB from the windows partition. And this saved my a**.

This needs to be marked [solved]


And should be a sticky somewhere.

---

