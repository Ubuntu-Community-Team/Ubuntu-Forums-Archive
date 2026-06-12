---
title: "Org is not installed? Java"
date: 2010-08-29
forum: General Help
---

### Post by Adrienk on 2010-08-29
I recently installed gtk+ for java on gnome. via sudo apt-get install libjava-gnome-java and after the installation i went to net beans, open it up and typed: import org.gnome.gdk.Event; I got a red line under the org part and a yellow line through out, meaning its an unused import. the red part is what I am concerned about:

the error message is as states - pakage import org.gnome.gdk.Event; does not exist.

but it has too because i installed the required packages from [http://java-gnome.sourceforge.net/4.0/get/ubuntu.php](http://java-gnome.sourceforge.net/4.0/get/ubuntu.php)

Can some one tell me whats going on?

---

### Post by Adrienk on 2010-08-29
bump to the top

---

### Post by akoskm on 2010-08-29
Have you added it to the build path?

---

### Post by Adrienk on 2010-08-29
I didnt think you had too. I feel dumb now lol, Because i could use org.GNOME but not org.gnome..

UM, in eclipse, how would you do such a thing?

---

### Post by akoskm on 2010-08-29
> **Adrienk said:**
> I didnt think you had too. I feel dumb now lol, Because i could use org.GNOME but not org.gnome..

UM, in eclipse, how would you do such a thing?

You can do such a thing in Eclipse by right clicking to your project and selecting Build Path > Configure Build Path. On the left side click to Add Library.
Select User Library hit Next, on the next dialog click to User Libraries... and create a New one, and with Add JARs specify the path to the given org.gnome.* libraries. Hit OK and check the box for this library.
The newly added library should appear in the Project view under the source folders.

---

