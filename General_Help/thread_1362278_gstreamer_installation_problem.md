---
title: "gstreamer installation problem"
date: 2009-12-22
forum: General Help
---

### Post by shariefbe on 2009-12-22
Hello i am newbie,
                I am trying to compile gstreamer for my MX515 board. But i am getting the following error as ```
checking for GST... no
configure: error: you need gstreamer development packages installed !

``` I dont know what is problem and what is missing here. Can anyone help me?

---

### Post by unmole on 2009-12-22
You probably need to install libgstreamer0.10-dev
But why do you want to complie gstreamer from source ? Does the version included in the repos not work ?

---

### Post by shariefbe on 2009-12-23
No i am trying to compile this gstreamer for my MX515 ARM board. Whta to do to install this gstreamer for my ARM board. And also i have to install video codecs for my ARM board.

---

### Post by unmole on 2009-12-23
Sorry. I did not realize you were cross compiling for an ARM board

---

### Post by shariefbe on 2009-12-23
No i am trying to compile this gstreamer for my MX515 ARM board. Whta to do to install this gstreamer for my ARM board. And also i have to install video codecs for my ARM board.

---

### Post by unmole on 2009-12-23
> **shariefbe said:**
> No i am trying to compile this gstreamer for my MX515 ARM board. Whta to do to install this gstreamer for my ARM board. And also i have to install video codecs for my ARM board.

I assume you got your tool chain ready if not see this [http://www.ailis.de/~k/archives/19-ARM-cross-compiling-howto.html]("http://www.ailis.de/%7Ek/archives/19-ARM-cross-compiling-howto.html")

Install the build depends on your host machine in this case libgstreamer0.10-dev

---

### Post by shariefbe on 2009-12-23
yes i have my cross compiling toolchain already. Now i am confused how to do the compile Gstreamer for my ARM board.

---

