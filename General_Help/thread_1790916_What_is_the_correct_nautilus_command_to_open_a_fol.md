---
title: "What is the correct nautilus command to open a folder not within the Home folder?"
date: 2011-06-25
forum: General Help
---

### Post by Paulgirardin on 2011-06-25
I am using an app called Unity-Launcher-Editor to create quicklists.

To add an quicklist entry for the Home folder launcher the app asks for the command to open it.
For the existing nautilus bookmarks the commands are: e.g. for Music it is "nautilus Music"

I have a nautilus bookmark called Data which opens the Data folder whose path is: /media/sda data/Data.

If I use the command "nautilus Data" I get the message "could not find "/Home/Me/Data when I use the quicklist entry.

I have tried the command: "nautilus /media/sda data/Data" but that doesn't work either.

Any suggestions?

---

### Post by flemur13013 on 2011-06-25
I'm not sure I'm reading your locations correctly, but: use quotes because of the space in the path?

$ nautilus "/media/sda data/Data"

If so, it might be a good idea to use a name w/o the space.

---

### Post by Bonster on 2011-06-25
or use a slash before the space like so

> xdg-open /media/sda**\** data/Data

---

### Post by Paulgirardin on 2011-06-27
The quotes weren't in the actual command -I put them there to show what the command I was using was.

sda data is the name of the volume the folder "Data" is on

I worked it out: the command should be **nautilus /media/sda4/Data**

And \ in front of any spaces.

Thanks for the help

---

### Post by mike555 on 2011-06-27
You might want to install "nautilus-open-terminal ",restart , then you can open terminal inside a folder ...........


 I might have miss read the post, anyway nautilus-open-terminal is good to have..

---

