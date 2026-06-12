---
title: "Charity network"
date: 2011-07-11
forum: General Help
---

### Post by davey_b on 2011-07-11
Hi folks, sorry if this is not the best section to post in but wasn't too sure where would be best to post.
 
I help out with a small charity and they are looking to sort out their network a bit. They have 9 PC's and one server and are looking to have a system where users can login to any PC on the network and be authenticated and get access to their own documents and different shares depending on what groups they are in etc. I was going to do this with Windows server and XP but it's looking a bit expensive and I was wondering what my options are for using ubuntu. 
 
Not too sure where to start so any help or pointers to documentations would be great.
 
Thanks
 
Dave

---

### Post by Bucky Ball on 2011-07-11
A Linux job indeed. This is definitely possible (if not advisable). The issue is, how long before they need the network up as you are going on a learning curve!

Firstly, you need Ubuntu Server install for the server and you need to work out how you are going to go about things (make a solid plan which, naturally, might alter a little along the way). Are all these machines identical (apart from the server)? If so, you can get one machine purring then install that config via the network to the others (or burn a disk of your install and do it that way).

Is server the gateway to internet? Server needs IP address and would be good idea to run all other machines with static IP addresses also. You can set up links on each machine to all the others (including the server). You can link to another machines partitions, or even specific folders.

Google 'setting up a server ubuntu' or something like that. Should give you some clues.

As I say, make a plan and start from the beginning by aquiring the knowledge you need for each step. Good luck. You'll be helping others on the forum by the end of this (and in the offline world, too, by the sounds of it) ... ;)

* Example:

Server: 192.168.0.1
Machine #1: 192.168.0.2
Machine #2: 192.168.0.3
etc. ...

... or however you want.

---

### Post by Surendil on 2011-07-11
Ubuntu server and SAMBA (PDC) might do the trick!

---

### Post by Bucky Ball on 2011-07-11
> **Surendil said:**
> Ubuntu server and SAMBA (PDC) might do the trick!

Samba not required as all Linux machines by the sounds (correct me if I'm wrong OP), but definitely possible. There are simpler ways. ;) (SSH, NFS, ...).

An SSH example for this, for instance, would entail:

Server: 192.168.0.1
Machine #1: 192.168.0.2
Machine #2: 192.168.0.3
etc. ...

Open Places>Connect to Server. Choose SSH from the drop down menu. Enter the IP address (192.168.0.3 to connect to machine #2), enter password, and that's it. (You could set it up to disable password also).

---

### Post by Surendil on 2011-07-11
> **Bucky Ball said:**
> Samba not required as all Linux machines by the sounds (correct me if I'm wrong OP), but definitely possible. There are simpler ways. ;) (SSH, NFS, ...).

Sure, SAMBA PDC config could be painful, but once you got it working it's much easier to apply changes.
At least, that's my point of view.

---

### Post by SeijiSensei on 2011-07-11
What will they do when you leave or get hit by a bus?  Will there be anyone there who can manage a Linux-based network?  

I know this will be considered heretical here, but you really should reconsider some flavor of Windows Server.  If your client is a charitable organization, you may be able to get ridiculously cheap deals on Windows software via a [reseller]("http://www.microsoft.com/licensing/licensing-options/charity-resellers.aspx") that specializes in charities.

---

### Post by davey_b on 2011-07-11
Thanks guys.   Looked into MS charity licenses and 'cause it's a Christian outdoor centre (faith based but open to everyone) you're not able to get really cheap MS charity stuff so it's still pretty expensive.
 
Re me getting hit by a bus :)  I have a partner in crime who will be doing this with me and he's a bit more clued up on Linux than me so he will be helping me with it.
 
With the setups you are describing will you have a login screen on each client and be able to log into the network like you might get on a windows server enviroment?
 
Ta

---

### Post by Bucky Ball on 2011-07-12
> **SeijiSensei said:**
> What will they do when you leave or get hit by a bus?  Will there be anyone there who can manage a Linux-based network?  



A total furphy, as we say in Australia. There are millions of organisations that would be lost if the network admin was hit by a bus, regardless of Win, Linux, or Mac or whatever their network is built on (heck, there's some folk who would be lost on their computer if the person at the next desk were hit by a bus)! 

Ever thought OP might actually find someone else who was interested in helping and learning and already at the organisation? Any network admin/sys admin who is familiar with Unix will find this setup a piece of cake, and there's zillions of them. ;)

Ever thought OP might simply go on holidays? Wouldn't make much difference whether Win or Linux network; in fact, Win would probably be more complicated, depending on how the Linux network is setup. 

Next point: Once set up, Linux network much less chance of going down than Win. Last point: Security. Windows network is like a bunch of leaky buckets. What happens when the network is infected while the OP is on holidays (or being hit by a bus)? That will call for a complete reinstall of the whole network!

As I say, a furphy.

---

### Post by Drenriza on 2011-07-12
> **davey_b said:**
> Hi folks, sorry if this is not the best section to post in but wasn't too sure where would be best to post.
 
I help out with a small charity and they are looking to sort out their network a bit. They have 9 PC's and one server and are looking to have a system where users can login to any PC on the network and be authenticated and get access to their own documents and different shares depending on what groups they are in etc. I was going to do this with Windows server and XP but it's looking a bit expensive and I was wondering what my options are for using ubuntu. 
 
Not too sure where to start so any help or pointers to documentations would be great.
 
Thanks
 
Dave

Giving you qualified help, without any plans of how the network architecture should be. Is like walking in blind. Personally i would not give advice to anyone, starting a project, with a server on a land and multiple hosts, with shares, security features and so on and so forth.

I don't mind help at all, but you need to tell "what is the plan". What exactly are they expecting, what is their budget and so on.

EDIT.
As i see above > What will they do when you leave or get hit by a bus? Will there be anyone there who can manage a Linux-based network? This is indeed a valid question. IF they don't have someone to maintain the network. Extensive documentation should be in order. So either when someone else comes in and maintain the network, he knows exactly what to do, based on the documentation created.

---

### Post by Bucky Ball on 2011-07-12
> **Drenriza said:**
> 
  IF they don't have someone to maintain the network. Extensive documentation should be in order. So either when someone else comes in and maintain the network, he knows exactly what to do, based on the documentation created.

Applies to any network, not just Linux, so for mine, still a furphy. ;)

---

### Post by Drenriza on 2011-07-12
> **Bucky Ball said:**
> Applies to any network, not just Linux

Ofc ,)

---

