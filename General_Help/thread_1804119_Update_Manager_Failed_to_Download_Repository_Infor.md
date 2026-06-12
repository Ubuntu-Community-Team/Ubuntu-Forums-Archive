---
title: "Update Manager Failed to Download Repository Information"
date: 2011-07-14
forum: General Help
---

### Post by OldBoy44 on 2011-07-14
Hi all,

Looking at Update Manager, it says that there may be updates available - at bottom of screen it says that there are no updates to install - (there have been several updates in the last three or four days). Upon pressing the check tab, the message appears "Failed to download Repository Information" with the following error message -
```

W:Failed to fetch http://ppa.launchpad.net/maltworld/compiz/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/maltworld/compiz/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```Is there anything I should do? If so - what?

Thanks for any help.

---

### Post by matt_symes on 2011-07-14
Hi

Open at terminal and copy and paste

```
grep -R http://ppa.launchpad.net/maltworld/ /etc/apt
```

Copy and paste the results back here. It will tell us where the offending line is.

Kind regards

---

### Post by OldBoy44 on 2011-07-14
Thanks Matt - here is output.

```

grep -R http://ppa.launchpad.net/maltworld/ /etc/apt
/etc/apt/sources.list.d/maltworld-compiz-natty.list.save:deb http://ppa.launchpad.net/maltworld/compiz/ubuntu natty main
/etc/apt/sources.list.d/maltworld-compiz-natty.list.save:deb-src http://ppa.launchpad.net/maltworld/compiz/ubuntu natty main
/etc/apt/sources.list.d/maltworld-compiz-natty.list:deb http://ppa.launchpad.net/maltworld/compiz/ubuntu natty main
/etc/apt/sources.list.d/maltworld-compiz-natty.list:deb-src http://ppa.launchpad.net/maltworld/compiz/ubuntu natty main
grep: /etc/apt/secring.gpg: Permission denied
grep: /etc/apt/trustdb.gpg: Permission denied

```

---

### Post by raja.genupula on 2011-07-14
> **matt_symes said:**
> Hi

Open at terminal and copy and paste

```
grep -R http://ppa.launchpad.net/maltworld/ /etc/apt
```Copy and paste the results back here. It will tell us where the offending line is.

Kind regards



hey matt
what about this , i think this can work for  solving that index crash 
      sudo rm -rf /var/lib/apt/lists/*
       sudo apt-get update

---

### Post by OldBoy44 on 2011-07-14
Thanks guys - with any help you will need to spell it out - I ain't too bright! :)

---

### Post by OldBoy44 on 2011-07-14
Matt, should I follow Raja's suggestion ? :D

---

### Post by matt_symes on 2011-07-14
Hi

The offending lines are in your sources.list file.

From the terminal type 

```
sudo nano /etc/apt/sources.list
```

Enter your password. It will not be echoed to the screen.

This will open the file in nano text editor.

Find the two lines
```

deb http://ppa.launchpad.net/maltworld/compiz/ubuntu natty main
deb-src http://ppa.launchpad.net/maltworld/compiz/ubuntu natty main
```

and delete then using  the delete key. Press CTRL + o at the same time to save the file and ctrl + x to edit nano.

Then type 

```
sudo apt-get update
```

You should then be good to go.

Kind regards

---

### Post by matt_symes on 2011-07-14
Hi raja.genupula

Hope you are well. That fix you detailed actually fixes a different issue. This issue is due to a PPA that does not exist in the sources.list file.

You can check this by typing the URL into Firefox

[http://ppa.launchpad.net/maltworld/compiz/ubuntu](http://ppa.launchpad.net/maltworld/compiz/ubuntu)

It will return a 404 error (not found).

Kind regards

---

### Post by OldBoy44 on 2011-07-14
Sorry to take so long - could find no lines with launchpad or maltworld in them

B.T.W. There was one line -
#deb [http://download.vbox.org/virtualbox/debian](http://download.vbox.org/virtualbox/debian) natty contrib
Should that be there?
I deleted Virtualbox a few hours ago.

---

### Post by matt_symes on 2011-07-14
Hi

Sorry mate. I must be going mad. :-k

The offending lines are in sources.list.d/maltworld-compiz-natty.list file and not in sources.list file. 

That is what you get when you try to do to many things at the same time ;) I must be getting old.

This will fix it for sure

Open a terminal and type

```
sudo rm /etc/apt/sources.list.d/maltworld-compiz-natty.list
```and then type 

```
sudo apt-get update
```

I will amend my previous post as it is irreverent.

Kind regards

---

### Post by matt_symes on 2011-07-14
Hi

> **aussiebean said:**
> Sorry to take so long - could find no lines with launchpad or maltworld in them

B.T.W. There was one line -
#deb [http://download.vbox.org/virtualbox/debian](http://download.vbox.org/virtualbox/debian) natty contrib
Should that be there?
I deleted Virtualbox a few hours ago.

That deb line is fine as it is commented out with the #.

Kind regards

---

### Post by OldBoy44 on 2011-07-14
All done - Thanks very much for your help Matt -

Note my previous comment about Vbox line - do I need to worry about it ? :)

---

### Post by OldBoy44 on 2011-07-14
> **matt_symes said:**
> Hi



That deb line is fine as it is commented out with the #.

Kind regards

Oops didn't see this  - Thanks again Matt :D

---

