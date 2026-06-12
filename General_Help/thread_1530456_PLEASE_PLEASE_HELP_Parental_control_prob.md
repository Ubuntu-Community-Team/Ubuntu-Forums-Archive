---
title: "PLEASE PLEASE HELP Parental control prob"
date: 2010-07-13
forum: General Help
---

### Post by azeem nawaz on 2010-07-13
can someone please tell me a way to password protect the HOSTS file in ubuntu so that when i block certain websites the other person cannot unblock them.
IMP: i donot want the HOSTS file to be protected by 'root' password as the other person knows it.
PLEASE help

---

### Post by davidmohammed on 2010-07-13
strange way to block websites - what browser are you using?

firefox has a number of [extensions]("http://kb.mozillazine.org/Parental_controls") you can use.  Is this the sort of thing you are looking for?

---

### Post by azeem nawaz on 2010-07-13
> **davidmohammed said:**
> strange way to block websites - what browser are you using?

firefox has a number of [extensions]("http://kb.mozillazine.org/Parental_controls") you can use.  Is this the sort of thing you are looking for?

NO i want the websites to be blocked system wide cause the person may use a different browser or for that matter disable the plugin

---

### Post by bodhi.zazen on 2010-07-13
> **azeem nawaz said:**
> can someone please tell me a way to password protect the HOSTS file in ubuntu so that when i block certain websites the other person cannot unblock them.
IMP: i donot want the HOSTS file to be protected by 'root' password as the other person knows it.
PLEASE help

If the other person has root access there is not anything you can do.

Potential solutions are to

1. first remove root access. Then use a proxy server. Personally I use privoxy + dansguardian.

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

Since the proxy is enforced via the use of iptables, they can use any browser they like, but they can not get around the proxy.

2. You may be able to configure your router to block web sites / content. If not, get a new router (routers with this capability are not that expensive).

3. Use a DNS service such as opendns.

[http://www.opendns.com/](http://www.opendns.com/)

4. Build your own firewall - it takes two network cards. You can then install squid / dansguardian what you want w/o having to purchase a new router.

---

### Post by mike555 on 2010-07-13
if you have dsl and a static ip you can set you modem to use opendns numbers and then go to opendns.com and they will let you block p2p, porn, etc.
 be sure to put password on modem ..

---

### Post by davidmohammed on 2010-07-13
first of all I would change the root password if the other person knows it.

Secondly, configure your network manager to use a DNS server such as OpenDNS - its free and you can tailor what sort of sites is generally available.

Thirdly, I would install a firewall - just type firewall in synaptic manager - for example "firestarter".  There you can define specific policies to block certain sites.

---

### Post by azeem nawaz on 2010-07-13
> **mike555 said:**
> if you have dsl and a static ip you can set you modem to use opendns numbers and then go to opendns.com and they will let you block p2p, porn, etc.
 be sure to put password on modem ..
Thanks but:
what if some one goes crazy at times and begins looking for things(porn) he ought not to. 
THE OTHER PERSON IS ME! 
NO SERIOUSLY!
is there a similar solution for that because i can even overcome this when i go mad
AND PLEASE DONOT WASTE YOURS AND MY TIME TELLING ME HOW I CAN SOLVE THE PROBLEM SPIRITUALLY ive spent too much time trying that

---

### Post by nothingspecial on 2010-07-13
In that case you have a few options.

Throw the computer away.

Accept that you like porn.

If it is a more serious problem than I think, this is not the place, get help.

When some people give up smoking they have to remove all cigarettes from the house, some people like to keep them around.

Maybe you just need to get rid of the computer.

---

### Post by davidmohammed on 2010-07-13
...

start using user accounts - on your account have full access controls - use network manager connection without opendns dns server.

On the other person accounts - restrict them with opendns and a firewall - make their account just a "user" account.  Make your account the "administrator"...

---

### Post by azeem nawaz on 2010-07-13
> **davidmohammed said:**
> ...

start using user accounts - on your account have full access controls - use network manager connection without opendns dns server.

On the other person accounts - restrict them with opendns and a firewall - make their account just a "user" account.  Make your account the "administrator"...
Ididnt get one word you said 
please explain
better english maybe

---

### Post by bodhi.zazen on 2010-07-13
> **azeem nawaz said:**
> Thanks but:
what if some one goes crazy at times and begins looking for things(porn) he ought not to. 
THE OTHER PERSON IS ME! 
NO SERIOUSLY!
is there a similar solution for that because i can even overcome this when i go mad
AND PLEASE DONOT WASTE YOURS AND MY TIME TELLING ME HOW I CAN SOLVE THE PROBLEM SPIRITUALLY ive spent too much time trying that

The problem is that there is not really a technological solution to that problem.

---

### Post by davidmohammed on 2010-07-13
user accounts - use the menu option administration - Users and Groups.

Create two users - one for yourself - one for the other person.

Assign yourself within the administrator group.  Assign the other user within the users group.

Login into your account. Right click network manager and edit the connection.  Enter the opendns IP address.  Click "available to all users". logout

Right click network manager.  Add a new connection with similar details as your normal network connection.  Make sure you dont have "connect automatically" ticked.

When you are having your "special" moment - connect to the internet through the new connection.

---

### Post by azeem nawaz on 2010-07-13
**davidmohammed: When you are having your "special" moment - connect to the internet through the new connection.**

'special' moment means that i cannot stop myself 
mannnn try to understand
i will use the same connection and not the new one because of the 'special' moment

i am hoping for a way to take preventive measures when i am 'normal' so i am 'blocked' from porn when i have a 'special' moment

---

### Post by davidmohammed on 2010-07-13
... troll territory here?

---

### Post by nothingspecial on 2010-07-13
> **davidmohammed said:**
> user accounts - use the menu option administration - Users and Groups.

Create two users - one for yourself - one for the other person.

Assign yourself within the administrator group.  Assign the other user within the users group.

Login into your account. Right click network manager and edit the connection.  Enter the opendns IP address.  Click "available to all users". logout

Right click network manager.  Add a new connection with similar details as your normal network connection.  Make sure you dont have "connect automatically" ticked.

When you are having your "special" moment - connect to the internet through the new connection.


That is not going to work for a special moment.

I know about addiction. If the opportunity is there and you are weak, you will get your fix.

This is not a self-harming addiction, in the sense of health, although if it conflicts with your spiritual ideals, can be extremely. 

And then the word "porn" has many meanings. Some things that can go under that description are unacceptable.

I don`t know what you are looking at and what your problem with looking at it is. I do know that this is not the place to discuss it.

If you have a computer with internet access and cannot stop looking at stuff that you don`t want to look at, then discard the computer and find professional help.

---

### Post by nothingspecial on 2010-07-13
I`m going to leave at this point.

If you are really an addict, then feel free to pm me.

If you are a troll ...........

.........oh, there`s loads of fun I could have.

Addiction to porn is like any other addiction, you try it, you like it, you use it more and more...... and like anything else it can lead to worse things.

Like I say, pm me. Ubuntu forums really isn`t the right place for this.

---

### Post by Iowan on 2010-07-13
> **bodhi.zazen said:**
> The problem is that there is not really a technological solution to that problem.There is probably very little that can be done under "normal" that can't be undone under "special" (short of having someone else oversee). 
Feel free to use the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123") to have the thread re-opened if there is something more to be gained.

---

