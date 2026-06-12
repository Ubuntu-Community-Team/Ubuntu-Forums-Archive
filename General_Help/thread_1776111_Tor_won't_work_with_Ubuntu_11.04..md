---
title: "Tor won't work with Ubuntu 11.04."
date: 2011-06-05
forum: General Help
---

### Post by pyromaniacwolf1994 on 2011-06-05
Hey everyone I tried to install Tor on my computer running Ubuntu 11.04, and when I try to run Tor I keep getting the same error message. While I would like to go to the support forums for Tor...I couldn't find any and figured this would be a good option since I'm trying to run Tor in Ubuntu....the error message I keep getting basically says that it can't listen in on port 127:0:0:1:9050 and then asks if Tor is already running which I know it isn't....any help would be very much appreciated. Thanks and have nice day.

---

### Post by Royce2u on 2011-06-09
> **pyromaniacwolf1994 said:**
> Hey everyone I tried to install Tor on my computer running Ubuntu 11.04, and when I try to run Tor I keep getting the same error message. While I would like to go to the support forums for Tor...I couldn't find any and figured this would be a good option since I'm trying to run Tor in Ubuntu....the error message I keep getting basically says that it can't listen in on port 127:0:0:1:9050 and then asks if Tor is already running which I know it isn't....any help would be very much appreciated. Thanks and have nice day.
Isn't anyone going to answer this man's question? I have been waiting and waiting for a reply. Have I missed a reply?

Here's my story:


I'm a newcomer to Ubuntu, and I need assistance with Tor.

I've installed Ubuntu 11.04 on my computer.

When I try to turn on Tor, Vidalia reports that another Vidalia process may already be running. However, my system monitor doesn't show that to a fact.

I am given the choice of continuing. When I do attempt to continue, the Vidalia control panel comes into view, and I see that Tor is not running. At that point, I repeat my effort to start Tor from the Vidalia control panel.

The result?

An “unexpected error” message manifests telling me that “Vidalia detected that Tor software exited unexpectedly. I'm advised to check the log for recent warning of error messages.

 I check the log and I am rewarded with the following feedback: “Warning Could not bind to 127.0.0.1:9050: Address already in use, Tor. 

Failed to parse/validate config. Failed to bind one of the listen... 

Reading config. Failed................


What should I do next?

---

### Post by linuxinstalledfromhdd on 2011-06-09
I don't use Tor anymore..  I tested it a long time ago.  It worked.  I used a plugin for firefox though to get it completely installed.  

What you should do however is post this message to the Tor newsgroups, or forums.  They should be able to help you with this..   I'm sorry nobody here knows at this time.

---

### Post by pyromaniacwolf1994 on 2011-06-09
Okay....I'll try to go to a tor forum...the only problem is I don't know of any and couldn't find any in a google search....would you mind sending me a link or two?

---

### Post by linuxinstalledfromhdd on 2011-06-09
> **pyromaniacwolf1994 said:**
> Okay....I'll try to go to a tor forum...the only problem is I don't know of any and couldn't find any in a google search....would you mind sending me a link or two?

Did you try searching in Google Groups?

---

### Post by jon zendatta on 2011-06-09
Don't think there is a forum..[https://blog.torproject.org/blog/]("https://blog.torproject.org/blog/")
If you want to browse try  Firefox addon -> foxy proxy
               email try [PHP]sudo apt-get install mixmaster[/PHP] :KS

---

### Post by pyromaniacwolf1994 on 2011-06-09
Yes I did.

---

### Post by pyromaniacwolf1994 on 2011-06-09
> **jon zendatta said:**
> Don't think there is a forum..[https://blog.torproject.org/blog/](https://blog.torproject.org/blog/)
If you want to browse try  Firefox addon -> foxy proxy
               email try [PHP]sudo apt-get install mixmaster[/PHP] :KS
Okay thanks

---

### Post by Royce2u on 2011-06-09
I looked over the Tor project page and didn't find anything to help with the issue of making Tor work for Ubuntu. Maybe if I start to beg the lads over there for help..........:)

I'm totally surprised that configuring for Tor isn't a major goal of people here. But...........I have been surprised before. Know that I don't mean my remark as a put down of anyone.

---

### Post by linuxinstalledfromhdd on 2011-06-09
I'm sure some users still use Tor.  I wouldn't since all the ends are monitored now.  It defeats the whole concept of privacy, imo.  I thought there was a better alternative to Tor these days?  I haven't really researched it, sorry to say. :)

Maybe someone has a suggestion?

---

### Post by SynonM on 2011-06-09
For anyone who wants Tor to work in Ubuntu 11.04
I had the same initial problems.
My tutorial is here...
[http://ubuntuforums.org/showthread.php?p=10918517#post10918517](http://ubuntuforums.org/showthread.php?p=10918517#post10918517)

hope that helps

remember though (there is no such thing as a secure network on the world-wide-web)
-technically speaking members of the Tor network (supposedly an anonymous network) can save your non encrypted Internet transmissions on their server/computer. (and there are ways of breaking SSL or TSL too.) soooo... it's never a perfect system....;)
So your are protected from people/companies knowing some of your information, but not the members you are using as relays on Tor.

---

### Post by SynonM on 2011-06-09
> **linuxinstalledfromhdd said:**
> I don't use Tor anymore..  I tested it a long time ago.  It worked.  I used a plugin for firefox though to get it completely installed.  
What you should do however is post this message to the Tor newsgroups, or forums.  They should be able to help you with this..   I'm sorry nobody here knows at this time.

I know...check here ...
[http://ubuntuforums.org/showthread.php?p=10918517#post10918517](http://ubuntuforums.org/showthread.php?p=10918517#post10918517)

---

### Post by SynonM on 2011-06-09
[U]sorry for the repost (I don't know if you can do this) here it is 
[/U]
The link above is the same thing

***---if done properly this should take less then 8 minutes---***

This is what I did...

stop all things related to Tor (or log off and log back in)

start terminal

```
sudo apt-get install aptitude
``````
 sudo aptitude reinstall  tor tor-geoipdb polipo vidalia -y
```go here and skip to step four  (4) do steps 4-6

[http://kyleabaker.com/2011/01/11/how-to-setup-and-use-tor-anonymity-in-ubuntu/](http://kyleabaker.com/2011/01/11/how-to-setup-and-use-tor-anonymity-in-ubuntu/)

and do this (quoted from [http://goshawknest.wordpress.com/2011/05/08/how-to-install-tor-on-ubuntu-natty-11-04/](http://goshawknest.wordpress.com/2011/05/08/how-to-install-tor-on-ubuntu-natty-11-04/)) 
(note: it is optional)
So it&#8217;s just uncommenting the two lines. **Tor** should be already working without any trouble, but it may be slow and u are not contributing to the **Tor** network. I highly suggest u to configure tor such that u can share your bandwidth with the network.
For changing this u have to modify */etc/tor/torrc *and change these two lines:[INDENT] #ORPort 9001
#DirPort 9030 
[/INDENT]into[INDENT] ORPort 9001
DirPort 9030 
[/INDENT]most importantly...

a program called Privoxy is known to interfere with Polipo
(I think it comes with a version of the Tor pkg but I don't know)

go to your terminal
```
sudo /etc/init.d/privoxy stop
``````
sudo /etc/init.d/polipo start
```next if you have not already goto  [https://www.torproject.org/torbutton/ ]("https://www.torproject.org/torbutton/")
then download the version of torbutton for your version of firefox (alpha = ff 4.0.1)
(stable = ff 3.)
start Vidalia
success = green onion 
start firefox 
Check for and then disable add-ons that might interfere with Tor button.
start or enable torbutton 


goto [https://check.torproject.org/](https://check.torproject.org/)
and if you don't get this
[IMG]http://img21.imageshack.us/img21/6713/screenshot2uon.png[/IMG]

I messed up or you did... :wink: ... let me know.

---

### Post by Royce2u on 2011-06-10
Although your advice wasn't  specifically directed at me, I followed your instructions and everything loaded into the terminal as required.  At that point, I thought I was “good to go.”.

Tor loaded up and the Vidalia panel informed me that I was successfully connected to the Tor network. However, when I went to the Tor project page and endeavored to confirm that I was really on the Tor network, the response was that I was not connected.

So I decided to restart my computer. After the restart, everything went back to square one--which is to say that Tor , once again, makes a rapid exit due to tor processes already running. But I can't imagine how it might still be the case.

Also, what is the command at the the terminal to check what is or is not running on my computer. I have been using a program that is tagged as “system monitor” to determine what is or is not running. Maybe it isn't “seeing” some aspect of Tor running when it actually is running.

Any and all suggestions will be appreciated. Thank you in advance.:o

---

### Post by SynonM on 2011-06-11
> **Royce2u said:**
> Although your advice wasn't  specifically directed at me, I followed your instructions and everything loaded into the terminal as required.  At that point, I thought I was “good to go.”.

Tor loaded up and the Vidalia panel informed me that I was successfully connected to the Tor network. However, when I went to the Tor project page and endeavored to confirm that I was really on the Tor network, the response was that I was not connected.

So I decided to restart my computer. After the restart, everything went back to square one--which is to say that Tor , once again, makes a rapid exit due to tor processes already running. But I can't imagine how it might still be the case.

Also, what is the command at the the terminal to check what is or is not running on my computer. I have been using a program that is tagged as “system monitor” to determine what is or is not running. Maybe it isn't “seeing” some aspect of Tor running when it actually is running.

Any and all suggestions will be appreciated. Thank you in advance.:o

Also, what is the command at the the terminal to check what is or is not running on my computer.  --> [http://ubuntuforums.org/showthread.php?t=514913](http://ubuntuforums.org/showthread.php?t=514913)

just use "system monitor" or "htop"

First of all I am assuming that Tor is green in the Vidalia for you and you can get connected now. The problem is communication from Tor to Tor-Button. Your browser is not being used through Tor.

 Secondly, I had the same problem, but unfortunately I don't know how to permanently stop the daemon Privoxy on startup. (Well I do, but I don't know what it might be affecting.)
I don't know exactly what the daemon does so I run this before starting Vidalia.

```
sudo /etc/init.d/privoxy stop
```

and Privoxy is a daemon so stopping the parent process may not be such a good idea.

Here is a GUI-program that lets you control start-up daemon's

```
sudo apt-get install sysv-rc-conf
 sudo sysv-rc-conf

```
  
Just be careful when editing the start-up daemon file.
I really don't know if you should stop all the pivoxy services or what. Trial and error I guess, just write down the original setup for you somewhere. (Hit spacebar to check and uncheck)

[IMG]http://img197.imageshack.us/img197/2326/screenshot3xy.png[/IMG]

---

### Post by Royce2u on 2011-06-12
SynonM

Many thanks for your excellent advice. After a couple of failures, I finally got Tor up and running! 

Thank you, thank you, thank you!:popcorn:

I was really pulling my hair for awhile, but all is well now!

Your efforts are greatly appreciated.

---

### Post by SynonM on 2011-06-13
> **linuxinstalledfromhdd said:**
> I'm sure some users still use Tor.  I wouldn't since all the ends are monitored now.  It defeats the whole concept of privacy, imo.  I thought there was a better alternative to Tor these days?  I haven't really researched it, sorry to say. :)

Maybe someone has a suggestion?

[http://www.quora.com/Are-there-any-alternatives-to-Tor](http://www.quora.com/Are-there-any-alternatives-to-Tor)

There isn't any alternative where your traffic isn't available to someone out there on the Internet. Unless you manually/virtually hook into some private servers (servers who's transfer information is not accessible to just anyone) and start your own encrypted transfers over a few of these routers from your *computer to the router* then and only after figuring that out could you truly access the Internet anonymously. Even then a good thing to remember is, "there is no perfect systems." 

Bottom-line if you want real anonymous browsing, get your own relays, and you would have to learn more on packets and transfer protocols so not to be traced. 

Also if you are willing to do all this, by searching/reading up books and cracking forums and getting info on usable servers for yourself, etc. you would probably be interested in doing some seriously illegal stuff which I would advice against.

---

### Post by Allavona on 2011-06-13
Instead of doing a full install of tor, repos and all, just use the tor browser bundle. It has everything you need. It is available on the torproject site.

---

### Post by ladi on 2011-07-03
> **linuxinstalledfromhdd said:**
> I'm sure some users still use Tor.  I wouldn't since all the ends are monitored now.  It defeats the whole concept of privacy, imo.  I thought there was a better alternative to Tor these days?  I haven't really researched it, sorry to say. :)

Maybe someone has a suggestion?


so the use of Tor is delusional?

---

