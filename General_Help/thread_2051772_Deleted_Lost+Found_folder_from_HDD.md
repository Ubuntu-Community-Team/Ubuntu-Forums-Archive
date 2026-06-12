---
title: "Deleted Lost+Found folder from HDD"
date: 2012-09-02
forum: General Help
---

### Post by fantab on 2012-09-02
I have an **Ext4 formatted** 1TB External Hard Drive [**ExHDD**].  The ExHDD is nearly full and I wanted to add some more files to it. 

When I saw that **Lost+Found** folder has taken up almost 33GB of Space I **DELETED **it, in hope that I would regain that space. Now, after deleting I see that the Space I had hoped will be available is not. The 33GB space seems "Lost" and cannot be "Found".


[LIST=1]
[*]Can this space be recovered? If YES then how? If NOT then:
[*]How can I get back my deleted Lost+Found folder?
[/LIST]
Thanks for your time.

---

### Post by Zvlwab on 2012-09-02
The Lost+Found folder is created every time an Ext4 partition is mounted if it doesn't exist yet. I think you need to shift+delete it, or use the delete it in the terminal using
```
rm -rf /path/to/Lost+Found
```

As far as I know it can be safely deleted, but it will reappear anyway.

---

### Post by fantab on 2012-09-02
> **Zvlwab said:**
> The Lost+Found folder is created every time an Ext4 partition is mounted if it doesn't exist yet. I think you need to shift+delete it, or use the delete it in the terminal using
```
rm -rf /path/to/Lost+Found
```As far as I know it can be safely deleted, but it will reappear anyway.

But can that space be freed up in any way to be used for storing files?

Also how is this Lost+Found different from .Trash?

---

### Post by spiky001 on 2012-09-02
Hi Hope this link helps with it,s desciption [http://askubuntu.com/questions/12286/delete-empty-lostfound-folder-automatically-if-its-empty](http://askubuntu.com/questions/12286/delete-empty-lostfound-folder-automatically-if-its-empty)

Also here [https://help.ubuntu.com/community/RecoverLostDiskSpace#A.27.27lost.2B-found.27.27_Folders](https://help.ubuntu.com/community/RecoverLostDiskSpace#A.27.27lost.2B-found.27.27_Folders)

To free up space you might have to empty trash. But check what is there 1st

---

### Post by fantab on 2012-09-02
Thanks Spiky,

I have tried connecting and reconnecting my ExHDD, and also restarted ubuntu with the Disk plugged in yet Lost+Found folder is not being re-created.

I had just deleted the L+F folder from gksu nautilus using just DELETE and not Shift+Delete... so I am a bit worried... because I neither have the space nor the said folder.

---

### Post by spiky001 on 2012-09-02
Did you open trash and see what is inside?

---

### Post by fantab on 2012-09-02
Firstly there is NO .Trash in ExHDD... Probably because I have never deleted anything from it.

Like I said I did NOT send L+F to Trash but Deleted it from Nautilus's Context menu with DELETE.

---

### Post by jmate24 on 2012-09-03
go to the external drive folder and press Control+H to show Hidden Files and Folders then click once on the .Trash-xxx icon and press Shift+Delete to get rid of those files then get Gparted in your Software Center.

Open Gparted and select your external drive in the top right corner and make sure your external drive is unmounted. Then right click your external partition in the bottom pane and select Check then click the Green Apply Check to procceed it will check your drive and replace the L+F Folder. 

You need the L+F folder for files that get lost or have errors when you Check your disk they can be found there but if you cannot recover them from there then you can delete the files in it with Shift+Delete.

Best of Luck...

jmate24

---

