---
title: "TOR will not install, I need to run a bridge to Iran-ASAP"
date: 2009-07-10
forum: General Help
---

### Post by democracyinpersia on 2009-07-10
Hey,  I am an American, born and raised in the USA but I know many Iranian people. I feel compelled to help out the Iranians tha are being repressed by the Islamo-Fascist government.  I do not have much money and while at work (I am not supposed too though) I read about The Onion Router and how relays are needed in order for people to send out information on the violence in Iran.  Using parts given to me by my friends, I put together an OK computer. I do not have enough money for Windows Vista and  heard dome good things about Linux, so I downloaded Ubuntu.   Long story short: I cannot figeur out how to install TOR on Ubuntu. Can anybody help me? I have &quot;jaunty&quot;.   Thanks in advance

---

### Post by michy99 on 2009-07-10
Read through this page and then post any questions you have.

[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

---

### Post by starcraft.man on 2009-07-10
You might also want these:

[https://www.torproject.org/docs/tor-doc-relay.html.en](https://www.torproject.org/docs/tor-doc-relay.html.en)

[https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)

Ignore the second links direction to compile from source (don't think needed), you can install the services by following the steps on the Ubuntu community wiki page above. The rest of page explains how to config server I believe, the ubuntu wiki page seems more geared towards client use. I can't really help beyond linking to documentation. TOR isn't really my thing, good of you to contribute though.

---

### Post by democracyinpersia on 2009-07-10
> **starcraft.man said:**
> You might also want these:

[https://www.torproject.org/docs/tor-doc-relay.html.en](https://www.torproject.org/docs/tor-doc-relay.html.en)

[https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)

Ignore the second links direction to compile from source (don't think needed), you can install the services by following the steps on the Ubuntu community wiki page above. The rest of page explains how to config server I believe, the ubuntu wiki page seems more geared towards client use. I can't really help beyond linking to documentation. TOR isn't really my thing, good of you to contribute though.
  I tried that before I posted. It asks me to input   deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main  but I do not know where to put that!

---

### Post by michy99 on 2009-07-10
Open your sources.list```
gksudo gedit /etc/apt/sources.list
```Add these lines to the file:```
deb http://mirror.noreply.org/pub/tor jaunty main
deb-src http://mirror.noreply.org/pub/tor jaunty main
```Save the file and exit.

Run these lines in terminal one at a time:```
gpg --keyserver subkeys.pgp.net --recv 94C09C7F
gpg --fingerprint 94C09C7F
gpg --export 94C09C7F | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install tor privoxy
```

Now edit the privoxy config file:```
gksudo gedit /etc/privoxy/config
```

Add this line:```
forward-socks4a / localhost:9050 .
```Make sure to include the period. Save and exit.

Enter these lines in terminal to start it:```
sudo /etc/init.d/tor start
sudo /etc/init.d/privoxy start
```

To use tor with firefox, I suggest using the FoxyProxy add-on.

---

### Post by Chronon on 2009-07-10
Once it's installed, read here:

[http://en.linuxreviews.org/HOWTO_setup_a_Tor-server](http://en.linuxreviews.org/HOWTO_setup_a_Tor-server)

---

### Post by joemun on 2009-07-10
Good luck!...

---

