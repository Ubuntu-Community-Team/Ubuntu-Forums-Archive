---
title: "Help needed regarding installation of JDK6u21"
date: 2010-07-18
forum: General Help
---

### Post by style_fantasy on 2010-07-18
HI, I'm an absolute beginner trying to sue Linux.
I just installed Ubuntu Linux Netbook Remix 10.04 LTS and everything's fine.
I just wanted to have Java in my Ubuntu. 
I downloaded JDK from Sun website. There are 2 files

jdk-6u21-linux-i586.bin
jdk-6u21-linux-i586-rpm.bin

I searched the web for instructions on how to install but I just get confused. 

Can anyone provide me with step-by-step installation including registering environment variable ?

Thanks !!!!

---

### Post by kerry_s on 2010-07-18
you don't need to do that.

you have 2 options.
1)
go to system-> synaptic package manager
type "restricted" on the top
install "ubuntu-restricted-extras"

that will give you most things you need, including the open source java.

2)
in synaptic click settings-> repositories
go to "other software" tab
check the one at the top & close
click the reload button
type "sun"
install "sun-java6-jre", it will pull everything in needed.

that will give you real java.

you can also do them both, you can have more then 1 java installed.

---

