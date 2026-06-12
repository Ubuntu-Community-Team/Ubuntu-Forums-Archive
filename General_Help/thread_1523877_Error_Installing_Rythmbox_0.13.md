---
title: "Error Installing Rythmbox 0.13"
date: 2010-07-04
forum: General Help
---

### Post by jt867 on 2010-07-04
Team,

 I am getting an error when I attempt to install rythmbox 0.13 on my Ubuntu 10.04.

Regards,

John...

---

### Post by maniandram on 2010-07-04
To install rhythmbox player just run "sudo apt-get install rhythmbox"(without the quotes).

---

### Post by dino99 on 2010-07-04
better to install a more stable one

---

### Post by jt867 on 2010-07-04
The Rythmbox that comes with Ubuntu is version 0.12 and it works fine, I just wanted to upgrade to the latest version.

John...

---

### Post by oldos2er on 2010-07-04
Don't use 'sudo' with ./configure.

You're missing some -dev packages the app needs to compile, that is what this "No package 'gstreamer-0.10' found

No package 'gstreamer-base-0.10' found

No package 'gstreamer-plugins-base-0.10' found" is telling you. See [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by mikewhatever on 2010-07-04
Why don't you post the error then?
Also, why do you think you need the 'more recent' version? Is anything wrong with 0.12?

---

### Post by jt867 on 2010-07-05
Guys,

 Thanks for your help. I received an email from the Rythmbox development team with the following instructions:

sudo add-apt-repository ppa:webupd8team/rhythmbox && sudo apt-get update
sudo apt-get install rhythmbox

I followed these instructions and the install was successful.

Regards,

John...

---

