---
title: "can I undo what I did?"
date: 2010-09-13
forum: General Help
---

### Post by Pacopag on 2010-09-13
Hi.  I was having trouble installing a program, so I tried a fix I found online, and it didn't work.  I was wondering if someone can help me undo what I did.  Here are the commands I ran to try to fix the problem.

cd /tmp	 

wget [http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb)

dpkg-deb -x ia32-libs_2.7ubuntu6.1_amd64.deb ia32-libs

sudo cp ia32-libs/usr/lib32/libstdc++.so.5.0.7 /usr/lib/  

cd /usr/lib

sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

Thanks.

---

### Post by 3Miro on 2010-09-13
```
 cd /tmp	

wget http://security.ubuntu.com/ubuntu/po...u6.1_amd64.deb

```
 This downloads a file into /tmp. This folder gets cleaned out regularly, so it should be fine to ignore it.

```

dpkg-deb -x ia32-libs_2.7ubuntu6.1_amd64.deb ia32-libs

```

This extracts whatever is in the file.

```

sudo cp ia32-libs/usr/lib32/libstdc++.so.5.0.7 /usr/lib/ 

```

This copies the extracted file libstdc++.so.5.0.7 into /usr/lib. Now "fixing" this depends, did you overwrite an already existing file or did you simply copy the file. If you copied the file, you can just delete it:
```
sudo rm /usr/lib/libstdc++.so.5.0.7 
```
however, if you overwrote a file, then you have to find out the package from which this file came in the first place and then reinstall the package (use System -> Admin -> Synaptic)

```

cd /usr/lib
sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

```
This creates a symlink, which is similar to a windows shortcut. You can delete it safely:
```
sudo rm /usr/lib/libstdc++.so.5 
```

I hope this helps.

---

### Post by Pacopag on 2010-09-13
That's perfect.  Thanks for your help.

---

