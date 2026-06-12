---
title: "Jabber and IRC servers."
date: 2006-01-31
forum: General Help
---

### Post by InsomniacUK on 2006-01-31
Hey everyone,

I am wanting to setup an IRC network and a Jabber server on my Ubuntu box. I have not done this before and would like some advice on how to do so, if anyone could help?

Ideally, I would like the IRC network to be distributed across several servers. Since my box is not online 24/7, I would like to share the load with the computers of some friends, so that the network remains online at all times, or at the very least, as much as possible. The same goes for the Jabber server.

I know there are free servers for both in the repositories (IRCd and ejabberd, for instance) but does anyone know if these will be suitable for what I require?

How do I go about configuring and managing the servers once installed?

Is there anything I need to know or should take into consideration?

Thanks in advance for anyone who can offer some advice. :)

---

### Post by Glarbl_Blarbl on 2006-02-14
I recently decided to tackle the same task, having recently switched to Ubuntu Breezy after years of wandering among Fedora,  Debian, and Slackware..

Ubuntu has mostly been great about working out-of-the-box for me, with a few unsurprising exceptions.  

Ejabberd has more recommendations that I can find, as it will do encryption and web-based administration.  I installed it a couple of days ago after trying jabberd briefly.  

It works with only a couple of hacks, you need to go into the /etc/ejabberd/ejabberd.cfg and put your hostname in where it tells you in the comments, comme ca:

[FONT=Times New Roman][SIZE=2]% Host(s) name: (replace for your hostname(s))
% Old {host, "localhost"}. option is equivalent to {hosts, ["localhost"]}.
{hosts, ["gps"]}.
[/SIZE][/FONT]

My server is called gps.  You'll also want to sudo and use "ejabberdctl register" to make yourself an account which you'll add into the same file for admin access.

[FONT=Times New Roman][SIZE=2]% Users that have admin access.  Add line like one of the following after you
% will be successfully registered on server to get admin access:
{acl, admin, {user, "g"}}.


[/SIZE][/FONT]Gotta love the one-character login, I use it whenever I can.  \\:D/

Once this is done issue the command: 
"[FONT=Times New Roman]sudo /etc/init.d/ejabberd restart[/FONT]"
and to double-check it's running:
"[FONT=Times New Roman]sudo ejabberdctl status[/FONT]"

Then fire up your favorite web browser and point it to
[FONT=Times New Roman]http://192.168.0.2:5280/admin/[/FONT] 
replacing 192.168.0.2 with the IP or hostname of your new ejabberd server.  For username, enter "user@server" where user is the account you made earlier with ejabberdctl and server is the hostname you inserted into the ejabberdctl.cfg file.  Hopefully you still remember the password you set from earlier. :-k

In the web admin panel you can set access controls and add users, it doesn't look like you can add modules from here though.  There's also a nodes page which is probably part of the fault-tolerance/rollover mechanism.  I don't have another server to test this aspect yet, maybe I will investigate and write further later.

The biggest bugaboo I encountered, though, was getting GAIM 1.5.0 to connect :p   ...  After a bunch of tries, I found that the only way to make it work was an account set up like this:

change **protocol** to Jabber 
**screen name** is user from before
** server** is the hostname from ejabberdctl.cfg
** resource** can be anything
** password** from before
** alias** is probably the name that shows up when you type a message
(open "**show more options**")
** check BOTH** TLS and SSL
** port** 5223
** Connect server** is IP or FQDN of your ejabberd server
** No Proxy**, unless you know that you need it.

Of course, now that you have the right settings you can actually just register a user from GAIM (unless you changed the acl already)...  It's nice to know how to do it from the command line though.

To add a buddy, make sure to do the full "user@server" formula, mine is g@gps ..

...

I'm not qualified to answer your question re: clustering of servers...  I guess the only reasons to use  your own servers/network for messaging are to keep total control of the logs/content sent and to get a much wider choice of user name (nothing to sneeze at ;)..    So the question becomes, is it worth it to you to go find out how to do this and teach your friends then help them implement it for the returns listed above?  The software can do it (within the limits of whatever hardware/bandwidth you have),  do you have the time to make it happen?

The configuration for one server is actually pretty easy compared to some slackware tasks (touchpad mouse, anyone?) I've done... So probably spreading ejabberd daemons across a few servers isn't much more than editing a few more config files once you know all the addresses you're going to use.
 
Hope this helps,
g

---

