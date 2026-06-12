---
title: "input/output error on external usb drive"
date: 2012-07-23
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-07-23
I am having problems copying a folder from a usb harddrive to my desktop.

I can copy a test file from the same directory, without errors. I migrated to the directory that contains the files I want, so I don't have a problem with the path.

I get the an error whether I try to drag and drop with a gui, or whether I try it from the terminal command.

I am running Xubuntu 11.10. 

The code is below, notice I copied readme.txt from the 'a' folder to my desktop without issues. But, using the same command with artie.zip gives me the input/output error.

```
artie@nowinderz-MS-7104:/media/Seagate/a$ ls
ls: cannot access artie.zip: Input/output error
11.10 entire disc  artie.zip  readme.txt
artie@nowinderz-MS-7104:/media/Seagate/a$ sudo cp readme.txt ~/Desktop
artie@nowinderz-MS-7104:/media/Seagate/a$ sudo cp artie.zip ~/Desktop
cp: cannot stat `artie.zip': Input/output error
artie@nowinderz-MS-7104:/media/Seagate/a$ sudo chown artie:artie artie.zip
chown: cannot access `artie.zip': Input/output error
artie@nowinderz-MS-7104:/media/Seagate/a$ 
```

Even when I try to change the owner of the '11.10 entire disc' folder, the input/output error on artie.zip causes the change of ownership to fail and I'm not even trying to access or modify the artie.zip file!!!!

I should say that the usb drive only has 16 GB free. The artie.zip file is 1.5 GB and the '11.10 entire disc' folder is 36 GB. My desktop punchbox has about 50 GB free.

The usb drive (source) is formatted in ntfs and the harddrive (destination) in my system is formatted in ext4.

I have no idea what's wrong. HELP please.

Art

---

### Post by dgharmon on 2012-07-23
> **goodbye-windows(tm) said:**
> I am having problems copying a folder from a usb harddrive to my desktop

From a BASH console try: ntfsfix .. see also ..  ntfs-3g

---

### Post by goodbye-windows(tm) on 2012-07-24
Thanks dg,

I don't have any idea what bash is, I'm having enough difficulty with terminal commands.

I did read up on it, so I have some idea what it's about now though.

But, I'm not ready to dive in to bash.

The drive in question is one of 2 USB backup drives and I wanted them both to be ext4 formatted anyway. So, I'm reformatting both drives and taking the opportunity to organize the data on the drives, they weren't organized well.

Regards,

Art

---

