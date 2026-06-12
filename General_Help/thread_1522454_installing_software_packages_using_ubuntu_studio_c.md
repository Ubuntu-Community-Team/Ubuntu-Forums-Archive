---
title: "installing software packages using ubuntu studio cdrom"
date: 2010-07-02
forum: General Help
---

### Post by maizuddin35 on 2010-07-02
Hello. linuxers

I have downloaded ubuntu studio 10.04 , and burn it into a cdrom. Is there any way in installing some software packages in ubuntu studio 10.04 in my ubuntu ?

---

### Post by labinnsw on 2010-07-03
Do a search of the disc for the application/s you want. Double click (or click) to install the package.

---

### Post by maizuddin35 on 2010-07-13
ok, now , I have Ubuntu 10.04 already installed in my pc, and then , I downloaded and burn ubuntu studio 10.04 . i just want to install some packages inside the ubuntu studio without actually installing everything inside my pc.

---

### Post by labinnsw on 2010-07-13
Problem
> **maizuddin35 said:**
> ok, now , I have Ubuntu 10.04 already installed in my pc, and then , I downloaded and burn ubuntu studio 10.04 . i just want to install some packages inside the ubuntu studio without actually installing everything inside my pc.

Solution
> **labinnsw said:**
> Do a search of the disc for the application/s you want. Double click (or click) to install the package.

---

### Post by snowpine on 2010-07-13
There is a much simpler solution. Ubuntu and Ubuntu Studio share the same software repository, therefore you can install any of the Ubuntu Studio applications using the Ubuntu Software Center or Synaptic Package Manager. If you want to install them all at once, search for "ubuntu-studio" and you'll find the audio apps, video apps, etc. are bundled as "metapackages."

This has the advantage of giving you the current version of the application, as opposed to the version that *was* current when the Ubuntu Studio CD was released.

Installing applications from the Ubuntu repository should always be your first choice. If that is not possible for whatever reason, and a work-around is required, it was not clear from your posting.

---

### Post by labinnsw on 2010-07-13
> **snowpine said:**
> If that is not possible for whatever reason, and a work-around is required, it was not clear from your posting.

I was thinking he wanted to use the CD as the title suggests.

---

### Post by maizuddin35 on 2010-07-14
im sorry for not giving such details to you guys, for your information, I have downloaded the ubuntu studio via my friend computer that have fast internet connection. I don't have the necessary stable internet connection so that i can install some of the packages inside my ubuntu.Thats why Ihave download and burn it into cd.

---

### Post by maizuddin35 on 2010-07-14
for the time being , i dont find any of clickable packages that i can install.

---

### Post by labinnsw on 2010-07-15
Please let me know one of the packages that you want to install and I will use it in a step by step example of how to do so.

---

### Post by maizuddin35 on 2010-07-15
How can I install hydrogen?

---

### Post by labinnsw on 2010-07-16
I have downloaded the ISO and verified that hydrogen is there. I am busy at the moment but, I will be doing the example soon.

---

### Post by labinnsw on 2010-07-16
Method 1

1. Insert the ubuntustudo disc.
2. Right click on the disc and select "Browse Folder"
3. Click the search icon on the toolbar
4. Type hydrogen in the search window
5. double click the hydrogen package in the search results.

(you should find that it is located at /media/Ubuntu-Studio 10.04 LTS amd64/pool/universe/h/hydrogen/hydrogen_0.9.4-1_amd64.deb if you downloaded the 64-bit ISO.)

Method 2

1. Insert the ubuntustudo disc.
2. Open a terminal (menu >> Accessories >> terminal) and enter the following codes ```
sudo apt-cdrom add
sudo apt-get update
```
3. Now you can install the package using Ubuntu software center or Synaptic, but the cd must be in the drive.

---

### Post by maizuddin35 on 2010-07-16
thanks for the reply, I will send some reply after i try to do it.

---

