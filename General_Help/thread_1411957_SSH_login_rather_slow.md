---
title: "SSH login rather slow"
date: 2010-02-20
forum: General Help
---

### Post by paopao on 2010-02-20
I apologize in advance that this problem is going to seem rather vague because I do not know what's going on.  Moreover, I'm still a newbie using Ubuntu, so I would appreciate very detailed instructions rather than vague suggestions that would be helpful to someone who wasn't as dumb as me.


I have several computers at my home: a laptop running Ubuntu 9.04, a desktop running 9.04 and a server running Ubuntu 9.10 server edition.  At home, the Internet comes to the modem and then to the wireless router (D-Link DIR-655), which then has a wire going upstairs to a switch (Netgear GS108 ) that then connects to the desktop and server.  The laptop sometimes it connected directly to the router via ethernet cable, or in the switch, or connecting wirelessly.

I noticed that anytime that I ssh between these various three machines in all the laptop's network configurations, there seems to be a delay between typing in ssh 192.168.1.x and being prompted for my password (or just logging in when using the key-based authentication).  The delay is about 7-10 seconds.  Not impossible to deal with, but annoying.

However, if I use other services on the computers (web (80), tranmission (9091)), the results are nearly instanteous.  Moreover, since my router has port forwarding set up for some of the ports, when I'm outside of my home and ssh using the external IP address, it is also instanteous.  Even if I'm at home and ssh via the external IP address, it's still pretty fast (<1 second).

This has always been a problem, so it's not like it was working when I first installed the operating systems and then stopped, I've just dealt with it.

So I'm asking if anyone has any ideas as to what could be causing these issues and what I could do to try to fix this?

Thank you.

---

### Post by gsparky2004 on 2010-02-20
Just so you understand, SSH is a secure protocol that requires authentication.  It requires that a certain amount of back-&-forth occur when first setting up the connection.  And a lot of it occurs before you're prompted for your password.  Personally, the 5-10 seconds you're seeing isn't bad.  That's normal, based on my experience.  I, too, also use SSH quite a bit between two desktops and a laptop.  This includes the use of SFTP so that I can access my files on my desktop (my primary computer) from anywhere.
If you want to get a better idea of all that is going on with SSH when you first enter the command, use the "-v", "-vv" or "-vvv" switches.  An example would be:
```
ssh -vv joe@192.168.1.100
```
The "-v", "-vv" and "-vvv" switches mean "verbose output" so that SSH outputs the various steps its taking along the way.  As you go from one "v" to 3 "v"s, the output becomes more detailed. 
Is there something you need to do that requires logging in via SSH, then logging back out over and over again?

---

### Post by paopao on 2010-02-20
Yeah, 7-10 seconds isn't a lot hence the reason that I've just dealt with it for awhile, but before I only had the laptop and desktop and would only ssh from the laptop to watch movies, since the desktop doubled as a server.  Now with the server in place, I find myself doing a lot more sshing (if that is a word).

My concern is that when I ssh into my machine from *outside* my home network, it goes much faster (counter-intuitive), so I'm guessing it might have to deal with something more than just the program, probably the router.

I did the verbose output and here is a section showing where it "hangs" for 7-10 seconds.  And by hanging, it flies through the first half of these messages, pauses for 7-10 seconds and then flies through the rest of the messages

```

.
.
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/paopao/.ssh/id_rsa (0x**********)
debug2: key: /home/paopao/.ssh/identity ((nil))
debug2: key: /home/paopao/.ssh/id_dsa ((nil))

(hangs here)

debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/paopao/.ssh/id_rsa
debug2: we sent a publickey packet, wait for reply
.
.

```When I use the external IP address, it does not hang at all, it flies continuously through all the messages.

And it's not just my user account, it also hangs for other accounts.  And I doubt that it's the key authentication because I've only done that recently (and as you can tell haven't finished and still have password authentications allowed) and this problem happened both before and after I set it up for paopao and still happens (and hangs at the same spot) for the accounts without keys.

---

### Post by gsparky2004 on 2010-02-20
Okay, I'm an idiot.  I didn't read your message carefully enough.  I completely missed the "from outside, I can get in instantaneously".  Plus, as a quick test, I timed my own SSH logins between a couple of my computers.  I'm also getting the <1 second login times.  I thought it took awhile.  It doesn't.  My bad.
Why does it work from outside the network, but not inside?  That's a good one.  My first thought was that perhaps MAC addresses are involved, but if you're using both wired and wireless and getting the same results regardless, that blows that theory out of the water.  I'm studying SSH as part of one of my masters program classes.  I'm going to research this one and I'll get back to you if no one else does.  (Just watch.  I'll post this reply, then a real expert will come in and say, "Hey, it's simple.  Just do XYZ")

---

### Post by amac777 on 2010-02-20
Hi, I did a google search and found this series of messages from someone having a very similar problem:

[http://lists.freebsd.org/pipermail/freebsd-questions/2005-June/089413.html](http://lists.freebsd.org/pipermail/freebsd-questions/2005-June/089413.html)

Just keep hiting next at the bottom to see all the responses and how s/he eventually solved it.

To summarize:

1. It seems like a reverse DNS problem. By default, SSH will check where incoming connections are from by performing a reverse DNS query on the incoming IP address. This will work fine when you come from an external computer, but might fail when you come locally if you don't have DNS setup properly. If you haven't done so already, you could try to add all your computer's hostnames and IP address in /etc/hosts on all computers (especially the ssh server) to make sure the reverse DNS will succeed. Obviously, you'd need to use static IP addresses on your LAN for that to work.

2. Failing the /etc/hosts solution above, you could try setting the UseDNS setting to 'no' in the ssh server. To do this:

```
sudo nano /etc/ssh/sshd_config
```

add this line to the bottom (or change the 'yes' to 'no' if it's already in the config file):

```
UseDNS no
```

then restart the ssh server:

```
sudo /etc/init.d/ssh restart
```

---

### Post by paopao on 2010-02-20
That really speed things up.  Now, I also don't need to type the IP address each time!  What would be really nice is if the router could somehow provide this information to all the computers so I don't have to edit all the /etc/hosts files whenever a new computer joins (although I admit going from 3->4 wouldn't require much work).


Just out of curiosity, since I did make static IP addresses for my computers, is there any security advantages/disadvantages to disabling the reverse DNS lookup?


Thanks!

It's OK gsparky2004 - thanks for the help.

---

### Post by amac777 on 2010-02-20
There might be a way to get your router to provide this information. It depends upon which router you have and if it supports some kind of a DNS server. Maybe login to your router and check through the available menus.

As for the security concern of disabling the reverse DNS lookup, for just a personal server I doubt it would do anything to security. Much more important would be using strong passwords or using only key based logins, making sure you have only the permitted ssh users specified as Allowusers in sshd_config, using fail2ban or some other mechanism to block hackers, and possibly even setting your router to only forward ssh connections from specific external IP addresses (if you only need access from fixed computers and you know their static IP addresses).

---

### Post by gsparky2004 on 2010-02-20
> It's OK gsparky2004 - thanks for the help!

No worries!  Like I said, just wait.  Someone with a clue will come along and provide the right answer!

---

