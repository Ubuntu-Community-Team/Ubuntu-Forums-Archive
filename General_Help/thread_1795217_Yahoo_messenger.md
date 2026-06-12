---
title: "Yahoo messenger"
date: 2011-07-02
forum: General Help
---

### Post by techbrainless on 2011-07-02
Hi All,
I am using Ubuntu 10.10 , I am looking for something like yahoo messenger (in windows) in which I can chat using yahoo chat rooms. 

I have tried pidgin but no way to enter to yahoo chat rooms.

Can you tell me the possible ways to do that.

---

### Post by Gryllida on 2011-07-02
Pidgin and Empathy (install "*telepathy-haze*" package too) can do that.

- [http://en.wikipedia.org/wiki/Yahoo!_Messenger#Compatible_software](http://en.wikipedia.org/wiki/Yahoo!_Messenger#Compatible_software)
- [https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/277360](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/277360) - workarounds for yahoo not working with pidgin

---

### Post by jim_deadlock on 2011-07-02
techbrainless, open your buddy list then go to Tools -> Room List

---

### Post by techbrainless on 2011-07-02
Thanks Gryllida for your reply ,

I have already installed pidgin , so shall I install empathy ? what is the next step i have to do ? how to install empathy with "*telepathy-haze*" package too


by the way i have tried to install empathy and got the following

```
sudo apt-get install empathy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  empathy: Depends: libatk1.0-0 (>= 1.20.0) but 1.12.4-3 is to be installed
           Depends: libebook1.2-9 (>= 2.22.3) but it is not going to be installed
           Depends: libempathy-gtk14 (>= 0.23.2) but it is not going to be installed
           Depends: libglade2-0 (>= 1:2.6.1) but it is not going to be installed
           Depends: libgtk2.0-0 (>= 2.12.0) but it is not going to be installed
           Depends: libpango1.0-0 (>= 1.20.3) but it is not going to be installed
           Depends: libpopt0 (>= 1.14) but 1.10-3 is to be installed
           Recommends: telepathy-gabble but it is not going to be installed
           Recommends: telepathy-salut but it is not going to be installed
           Recommends: telepathy-stream-engine but it is not going to be installed
           Recommends: gvfs-backends but it is not going to be installed
E: Broken packages

```

---

### Post by jim_deadlock on 2011-07-02
Empathy sucks (IMO), did you try what I suggested with Pidgin? The chatrooms are right there, I went into one just to test it and got bombarded with people wanting to show me their cams etc so it works just fine. I won't be going back there myself but hey, whatever floats your boat :)

---

### Post by techbrainless on 2011-07-03
Thanks jim_deadlock 
 				 				[]("http://ubuntuforums.org/member.php?u=1108068")
>  		techbrainless, open your buddy list then go to Tools -> Room List 	

the matter is more easier then what i have expected.

I have got the room list , and it worked for me

Thanks again for all.

---

