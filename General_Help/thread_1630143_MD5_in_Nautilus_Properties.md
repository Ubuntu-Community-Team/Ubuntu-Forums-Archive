---
title: "MD5 in Nautilus Properties"
date: 2010-11-24
forum: General Help
---

### Post by HappySmack on 2010-11-24
I had on my last box, the ability to check md5 and other digests from the properties of a given file. I am now on a fresh install of 10.10 and have been unable to restore this function.  I do not even remember if it was a script that I added or a package that I installed. Searches of Google, Ubuntu and, Synaptic have proven unfruitful. I have attached a screenshot to show the implementation of it.

---

### Post by ianc1 on 2010-11-24
I think what you are looking for is the python-nautilus application which can be installed through Synaptic.  Once installed look in /usr/share/doc/python-nautilus/examples and you will find md5sum-property-page.py and open-terminal.py.  These will need to be copied to /home/username/.nautilus/python-extensions the last directory will probably need to be created.  Once put there I think you'll need to log out and in again for this to take effect.

The open-terminal.py adds the open terminal here to the right click option in nautilus which I use loads I assume (95 % sure) that the md5sum-property-page,py is what you need.

Ian

---

### Post by ianc1 on 2010-11-24
I've just checked on my machine and the instructions detailed in my previous post add an md5sum tab only to the right click > Properties option.

---

### Post by HappySmack on 2010-11-24
Thanks for the quick reply. I know of this or similar to it. I am looking for the exact instance I have in the attached picture.

---

### Post by ianc1 on 2010-11-25
Please post back if you find it as the attached image (which I did not notice prior to posting) looks interesting.

---

### Post by ianc1 on 2010-11-25
Hah.  Having now used the python-nautilus md5sum tool I suggested I find that the md5sum it yields is different to that obtained by doing md5sum filename.

A quick mess around in Python reveals (fairly sure anyway) that it's simply doing a hash of the string absolute file path.  So if the file is /home/username/file1.txt its simply hashing the text "/home/username/file1.txt" not the file.  Looking at the file md5sum-property-page.py also looks like this is what's happening as the file does not appear to be read anywhere.  My Python is pretty basic but I think I'm right.  Some one please correct me if not.

This means I'm now all the more intrigued as to what the package was you were using before.

---

### Post by HappySmack on 2010-11-25
Still not having any luck.

 Looking in the /usr/lib/nautilus/extensions-2.0 directory has provided no help.

 I just hooked the old box up, next to my current setup. So if anyone can point me in a direction to look for this, I would be indebted.

 Also, I exported a list of ALL installed packages. I have gone through the list and searched for anything that seemed promising. I came up with nothing. I attached the list to this post.

---

### Post by HappySmack on 2010-11-26
Answer found by Takkat at askubuntu.com. It is a function of gtkhash. The part I overlooked was, You need to select whatever hashes you desire in the preferences and they are then displayed in a newly created "Digests" tab in a file's properties.

---

