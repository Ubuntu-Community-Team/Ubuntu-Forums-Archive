---
title: "Bitlbee on Ubuntu help please"
date: 2010-05-29
forum: General Help
---

### Post by dinonet on 2010-05-29
Hi guys, I'm still learning things the hard way with ubuntu and some programs and was hoping someone could help me figure this one out. I;ve been using bitlbee andits been great until they messed up msn and now I need to upgrade to version 1.2.7. I have 1.2.3 now. I downloaded it and did ./configure, make (seemed to compile everything), then sudo make install. It spits out the following:

mkdir -p /usr/local/sbin/
install -m 0755 bitlbee /usr/local/sbin//bitlbee
make -C doc install
make[1]: Entering directory `/home/lamer/bitlbee-1.2.7/doc'
mkdir -p /usr/local/share/man//man8/ /usr/local/share/man//man5/
install -m 0644 bitlbee.8 /usr/local/share/man//man8/
install -m 0644 bitlbee.conf.5 /usr/local/share/man//man5/
make -C user-guide install
make[2]: Entering directory `/home/lamer/bitlbee-1.2.7/doc/user-guide'
mkdir -p /usr/local/share/bitlbee/
chmod 0755 /usr/local/share/bitlbee/
rm -f /usr/local/share/bitlbee//help.txt # Prevent help function from breaking in running sessions
install -m 0644 help.txt /usr/local/share/bitlbee//help.txt
make[2]: Leaving directory `/home/lamer/bitlbee-1.2.7/doc/user-guide'
make[1]: Leaving directory `/home/lamer/bitlbee-1.2.7/doc'


And then nothing else. I try to run bitlbee and its my old version. I've looked everywhere for instructions but couldn't get anywhere. Can someone put me in the right direction? I'm sure I'm doing something wrong. Any help would be greatly appreciated. Thanks.

---

### Post by ba_saish on 2010-05-31
I am not sure if this is the issue but may be your executable in the /bin is still pointing to the older version. try running the executable present in the installation folder and see which one starts.

---

### Post by dinonet on 2010-06-01
> **ba_saish said:**
> I am not sure if this is the issue but may be your executable in the /bin is still pointing to the older version. try running the executable present in the installation folder and see which one starts.

Hi, thanks for your response. I am still a bit of a newbie, would it be the file "bitlbee" in the install folder that is the executable? How could I run it? 

Thanks!

---

