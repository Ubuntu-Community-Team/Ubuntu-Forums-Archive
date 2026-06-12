---
title: "How to edit stuff in file systems"
date: 2012-01-13
forum: General Help
---

### Post by the great sayaman on 2012-01-13
I am currently running ubuntu 11.10 for a short while on my laptop before which i was running 10.04

i tried nautilus but the problem is even with that i am unable to paste anything in file systems so is there any way that i could be able to paste things in folders contained in file systems 

actually what im trying to do is in this: [http://www.omgubuntu.co.uk/2011/12/how-to-customise-unity-like-never-before/]("http://www.omgubuntu.co.uk/2011/12/how-to-customise-unity-like-never-before/")
 im in the part where you have to replace a few files in usr\share\unity\4 but i am unable to paste things in it

---

### Post by the great sayaman on 2012-01-14
I have a serious problem now please someone reply

i went into nautilus and cut the following files from usr/share/unity/4

[LEFT]*squircle_base_54.png*, *squircle_shine_54.png*, *launcher_bfb.png*, *launcher_icon_back_54.png*, *launcher_icon_edge_54.png*, *launcher_icon_glow_62.png*, *launcher_icon_shine_54.png*, *find_files.png*, *find_internet_apps.png*, *find_media_apps.png*, *find_more_apps.png*[/LEFT]


i was not able to paste them back as that option was unavailable and then i got really annoyed as i was not able to paste the new files in their place either as the above link says so i restarted.

when i restarted unity just did not start and i got an absolutlly blank screen with just the desktop available 

i dont know how to reverse the changes as now i cant even go anywhere. Right now i am on the live cd but i dont have permission to edit anything in this**

---

### Post by carl4926 on 2012-01-14
Are those files in the live session at usr/share/unity/4 ?

---

### Post by the great sayaman on 2012-01-14
> **carl4926 said:**
> Are those files in the live session at usr/share/unity/4 ?

im not sure what you mean by the live session

---

### Post by carl4926 on 2012-01-14
> Right now i am on the live cd

Open the file system of the live session
Are the same files present?

You could use them to copy to your actual install

---

### Post by the great sayaman on 2012-01-14
> **carl4926 said:**
> Open the file system of the live session
Are the same files present?

You could use them to copy to your actual install


i found the files on the live cd but how do i copy them to the actual install??

---

### Post by carl4926 on 2012-01-14
Here
Download this
[http://dl.dropbox.com/u/10573557/4.tar.gz](http://dl.dropbox.com/u/10573557/4.tar.gz)

Extract the folder 4

copy the contents over

I think you are struggling with getting permissions, am I correct?

The way I would do it is to delete 4 in your main file system
Then mv the folder I gave you over

```
sudo rmdir /usr/share/unity/4

```
```
sudo mv 4 /usr/share/unity/
```

**Note: In each case you must be working from the correct directory
You need to be careful!
Because you will have to add to the paths I listed because you are working from a Live CD

If in doubt wait and ask for advice. I have to go out now.

---

### Post by the great sayaman on 2012-01-14
> **carl4926 said:**
> Here
Download this
[http://dl.dropbox.com/u/10573557/4.tar.gz](http://dl.dropbox.com/u/10573557/4.tar.gz)

Extract the folder 4

copy the contents over

I think you are struggling with getting permissions, am I correct?

The way I would do it is to delete 4 in your main file system
Then mv the folder I gave you over

```
sudo rmdir /usr/share/unity/4

``````
sudo mv 4 /usr/share/unity/
```**Note: In each case you must be working from the correct directory
You need to be careful!
Because you will have to add to the paths I listed because you are working from a Live CD

If in doubt wait and ask for advice. I have to go out now.

i did what you asked me but when i did the suco rmmdir /usr/share/unity/4 then this came up

rmdir: failed to remove `/usr/share/unity/4': Directory not empty

---

### Post by carl4926 on 2012-01-14
I thought you had emptied it
Tell you what, just rename it with

```
sudo mv /usr/share/unity/4 /usr/share/unity/4-old
```Just in case there is something in there you need later

Then move the folder I gave you as directed

---

### Post by the great sayaman on 2012-01-14
> **carl4926 said:**
> I thought you had emptied it
Tell you what, just rename it with

```
sudo mv /usr/share/unity/4 /usr/share/unity/4-old
```Just in case there is something in there you need later

Then move the folder I gave you as directed

im in the live cd and that code did nothing but change the name of the 4 in the live cd and did nothing to the one in the 498 GB Filesystem
thats the one i need to change the one in the 498 GB Filesystem

---

### Post by the great sayaman on 2012-01-14
could someone please help me ive been sitting for the past 4 hours and my problem is still there

[-o<

---

### Post by carl4926 on 2012-01-14
Look
You don't seem to understand some stuff. So lets try something easier for you.

I suggest you get the folder I uploaded for you. Put it on a pen drive.

Now get Parted Magic and burn it to a cd and boot it. [http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)
It will let you mount your Ubuntu partition to have access and copy the folder I gave you

---

### Post by KdotJ on 2012-01-14
Edit: Didn't properly read first post!

---

