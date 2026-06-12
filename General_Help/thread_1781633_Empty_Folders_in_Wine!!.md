---
title: "Empty Folders in Wine??!!"
date: 2011-06-13
forum: General Help
---

### Post by tossknobber on 2011-06-13
Hello

I am new to ubuntu. I have just installed Ubuntu 11.04 on my lenovo g550 laptop. Everything runs and looks great. I have installed Ubuntu alongside Windows 7 and I wish to access my files and folders that are in Windows.
I installed Wine and I have pointed it to my C: drive.
It picks this up fine, and I cant browse through the folder structure without a problem. However, when I go to look at my personal files (i.e. within My Documents) all of the folders are empty. The Windows folder on the C: drive has both files and folders, by C:/Users/Dave/My Documents or My Music or any of the other folders are all empty!!! Is there is a reason for this, and is there a way for me to see and access my files from within Ubuntu?? Any help would be greatly appreciated.




Thanks

Dave

---

### Post by flick on 2011-06-13
If I recall correctly, Wine sets up a "fake" C drive to install Windows programs to. You should be able to browse to data on your actual Windows installation just by using the plain old file manager. Fire that up, click on "File System", see if you can see and browse to your Windows partition.

---

### Post by Karlchen on 2011-06-13
Hello, Dave.

I am afraid that you misunderstand the purpose of Wine. :(

Wine is not meant to permit you to access your Windows system from withing Linux. Wine is meant to permit you to install and run Windows applications inside Linux. :idea:
To learn more on Wine, please visit [**the Wine homepage**]("http://www.winehq.org/").
If you use Wine in order to go to "My Documents", what you will be presented is _not_ your "My Documents" foldertree on your Windows drive, but it is the Wine internal "My Documents" foldertree, which is located somewhere below /home/<your Linux username>/.wine.

What you wish to do, accessing the Windows partition(s) from inside Linux, is possible, too, yet, it does not involve Wine at all.

As you have not given too many details on how you have installed Windows 7 and Ubuntu on the same machine, I will assume that Windows is located on the first partition and Linux on the second partition.

Provided you have got access to a standard Ubuntu file manager like Nautilus or like Thunar, accessing the Windows partition from inside Ubuntu is pretty trivial: Assuming the volume name of your Windows 7 drive is "System", the file manager will allow you to simply go to "System". Doing so will mount the Windows partition under /media/system.

In order to go to your documents folder you navigate to /media/system/users/<your Windows account name>/documents.

Sorry I cannot be more precise at this moment, because I am typing this reply from a Windows 7 machine, no Ubuntu on this machine.

HTH nevertheless,
Karl

---

