---
title: "Transfering symlink targets over sftp"
date: 2012-06-18
forum: General Help
---

### Post by kristianz on 2012-06-18
Hey!

I want to share some files with a friend. I've set up a limited user account on my computer ("server") running Kubuntu 12.04 and my friend's computer ("client") runs Ubuntu 12.04.

On the client, I've added a sftp://... bookmark in Nautilus, ssh-keys to connect to the server. It works fine: My friend clicks the Nautilus bookmark, types in the keyphrase to unlock the ssh-key (with seahorse, I presume) and the remote sftp target mounts, and he can browse it.

It seems to me a convenient way to share files would be to have a folder which the client has sftp access to, then throw into that folder symlinks to the actual content I want to share.

Problem: The client sees these symlinks as symlinks, and they are transferred as such. They are symlinks to targets on the server, and are as such useless on the client. Is there any way I can set up either the client or the server so that the targets of the symlinks are transferred instead of the symlinks themselves?

I know there are other ways to share files, but it has to be easy to use on the client (my friend is no geek) and secure. If the above problem is not solvable, I'd welcome suggestions for other ways to set up (one-way) file sharing for my friend.

---

### Post by kristianz on 2012-06-30
Bumping this. To recap, when browsing an sftp mount, opening symlinks on the host are just transmitting the links, not the file to which the links point. 

There's an option to follow symlinks when mounting with fstab or the CLI, but I'm setting this up for a less competent user and want to use a sftp:// bookmark in Nautilus. Any way to have symlinks on the host transmitted as the target file (or browsed as the target folder), not just symlinks?

---

### Post by Morbius1 on 2012-06-30
I do not know the answer to your question but since you haven't received any answers in a week I have a suggestion: Don't use symlinks - use bind instead. Let's say you have a folder: /Shared that you want the remote user to access. And you want to have a symlink to say: /Data

Create a subdirectory within /Shared called /Shared/Data. Then as a temporary test "bind" /Data to /Shared/Data:
```
sudo mount --bind /Data /Shared/Data
```[COLOR=Blue]*Note1: This is not like a symlink it's like a real mount. Deleting something or change permissions on /Shared/Data changes /Data as well.*[/COLOR]

[COLOR=Blue]*Note2: To undo this temporary mount:*[/COLOR]
```
sudo umount /Shared/Data
```If that accomplishes what you want then create an Upstart job to have this done on boot:

Create an upstart file:
```
gksu gedit /etc/init/bind-remounts.conf 
```And add the following to the file:
```
# Remount partitions with bind
#
description "Bind Directories to Shared Folder"

start on stopped mountall

script
mount --bind /Data /Shared/Data
end script
```Admittedly it's more work to do it this way but once the upstart file is created you can add to the file other binds like this:
> script
mount --bind /Data /Shared/Data
mount --bind /home/morbius/Music /Shared/Music
end scriptJust make sure the mount point of the bind ( i.e., /Shared/Music ) exists first.

---

### Post by kristianz on 2012-06-30
Thanks for the suggestion! That's actually what I've been doing (except I used fstab) while trying to work out a better solution.

The problem with this solution is that it's cumbersome to share many folders this way (and too difficult for anyone else in the household but me to add folders to share), so I instead opted to share more generously than I'd prefer (all of my media content, all of my pictures, etc.). I'd much prefer to pick individual subfolders to share by adding symlinks to them. That would be quick for me to do and easy enough for my girlfriend to do.

But thanks for your reply in any case!

---

