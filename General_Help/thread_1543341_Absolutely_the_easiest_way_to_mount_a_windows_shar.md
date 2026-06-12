---
title: "Absolutely the easiest way to mount a windows share in Ubuntu"
date: 2010-07-31
forum: General Help
---

### Post by nmyrick on 2010-07-31
Here is absolutely the simplest way to mount a Windows share on a home network from an Ubuntu computer.  This does not involve opening the terminal at all.

1.  Click on the 'Places' menu

2. Click 'Connect to a Server' (this works even if you don't have a server on the network)

3. Under 'Service type' select 'Windows Share'

4. In the Server text box, enter the ***computer name*** of the computer that contains the share folders

5. Click 'Connect'

Thats it!  Now, when you click on the Places menu, select Network, and all of the computers that contain windows shares on your network will appear!

Now, in order to access the share folder, double click the name of the computer where the share is located, then double click the share.

Note:  It may take a couple of times of clicking the computer and the share, and it may throw you a couple errors, but it will mount the computer and the share after the second or third try.  I think it just times out while trying to mount the share sometimes and just says that it can't mount the share, even though it eventually does.

---

### Post by dixcuxx on 2011-07-27
How about if the Windows share setup requests username and password to have access right?

---

### Post by nmyrick on 2011-07-28
Is it asking for the username and password?  I know that if you connect a Windows FAT32 or NTFS drive to an Ubuntu computer, Ubuntu does not recognize Windows permissions and has full access to all the files, but I don't know if that's the case on a network share.

---

