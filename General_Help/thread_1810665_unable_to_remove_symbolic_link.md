---
title: "unable to remove symbolic link"
date: 2011-07-23
forum: General Help
---

### Post by vichingo_nl on 2011-07-23
Hi,

I created the following symbolic link:

```
ln -s /home/vichingo/.gvfs/"media on mybook" /media/mybook
```this worked, only now I have a folder media on mybook within the mybook folder.

I wanted to remove this link, but when doing:

```
sudo rm /media/mybook/media on mybook
```I get:

```
rm: cannot remove `/media/mybook/media': No such file or directory
rm: cannot remove `on': No such file or directory
rm: cannot remove `mybook': No such file or directory
```for some reason I am either unable to remove the link or change the name of the folder to change the spaces into underscores.

I have to note that I am a beginner Linux user.

Could anybody help me sort out this problem?

---

### Post by galvatron408 on 2011-07-23
Type the following

sudo rm /media/mybook/m

when you get to the m like above, press tab and let bash fill it in for you.

---

### Post by lmarmisa on 2011-07-23
Type this command:

```

rm '/media/mybook/media on mybook'

```

---

### Post by lmarmisa on 2011-07-23
Hmmmm.

The symbolic link is **/media/mybook**.

The directory '**/home/vichingo/.gvfs/media on mybook**' is the automatic mount point created by GVFS. So, your question is not accurate, IMHO.

Best regards,

Luis

---

### Post by jocko on 2011-07-23
> **lmarmisa said:**
> Hmmmm.

The symbolic link is **/media/mybook**.

The directory '**/home/vichingo/.gvfs/media on mybook**' is the automatic mount point created by GVFS. So, your question is not accurate, IMHO.

Best regards,

Luis
Did you not read the first post?
He tried to make the link /media/mybook, but instead he got the link "/media/mybook/media on mybook".
His question is how he can remove that link. This is how:
```
rm '/media/mybook/media on mybook' 
```The ln command can be a little bit ambigous.
In this command:
```
ln -s /path/to/file1 /path/to/file2
```The first path is always interpreted as the target file, while the second path is either interpreted as the link name or just the path to where the link should be. If there is already a directory with the same name as the intended link, the link will end up in that directory, but get the name of the target file...
So depending on whether or not there is a folder with the name 'file2', it will either create the link '/path/to/file2' or the link '/path/to/file2/file1'...

---

