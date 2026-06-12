---
title: "Tor + Polipo Help Please"
date: 2011-07-04
forum: General Help
---

### Post by Jabrick on 2011-07-04
Hello I had polipo and tor working perfectly!
So I was using it just surfing the web and all of a sudden firefox kept saying the connection timed out.
I didn't do anything at all to cause this!!!
Why is this not working anymore?
This happened when I used privoxy instead of polipo too.
It worked in the beginning and then just didn't for no reason.
Can someone please help me out, I'm very frustrated!

---

### Post by Dangertux on 2011-07-04
Make sure polipo and privoxy are not running at the same time ; it will cause TOR to fail.

---

### Post by Jabrick on 2011-07-04
> **Dangertux said:**
> Make sure polipo and privoxy are not running at the same time ; it will cause TOR to fail.

They are not, I already uninstalled privoxy from my computer due to frustration. I was hoping polipo would go much smoother, but only for 10 minutes :(

Thank you for replying makes me feel better, but still very mad.

---

### Post by Enigmapond on 2011-07-04
> **Dangertux said:**
> Make sure polipo and privoxy are not running at the same time ; it will cause TOR to fail.

+1 I would advise use one or the other and remove the one you don't. They conflict. Check the polipo config. /etc/*polipo*/[I]config And if you need a good working template [I]It can be got here:

[http://www.pps.jussieu.fr/~jch/software/polipo/config.sample]("http://www.pps.jussieu.fr/%7Ejch/software/polipo/config.sample")

Just copy and paste it in it's entirety.

Cheers!

EDIT: Install also Vidalia as it give you a bit more control.
[/I][/I]

---

### Post by Jabrick on 2011-07-04
> **Enigmapond said:**
> +1 I would advise use one or the other and remove the one you don't. They conflict. Check the polipo config. /etc/*polipo*/[I]config And if you need a good working template [I]It can be got here:

[http://www.pps.jussieu.fr/~jch/software/polipo/config.sample]("http://www.pps.jussieu.fr/%7Ejch/software/polipo/config.sample")

Just copy and paste it in it's entirety.

Cheers!
[/I][/I]

Yes I have removed privoxy, and I used the config file you suggested, but still nothing is working. I am very confused because it was working fine, until ten minutes or so in. What is going on!?!?! :(

Also I tried vidalia but when I try to start up tor from vidalia it gets stuck on starting network.

---

### Post by Dangertux on 2011-07-04
> **Jabrick said:**
> Yes I have removed privoxy, and I used the config file you suggested, but still nothing is working. I am very confused because it was working fine, until ten minutes or so in. What is going on!?!?! :(

Also I tried vidalia but when I try to start up tor from vidalia it gets stuck on starting network.


Try verifying that polipo is running and bound properly. Check netstat by default it should bind to port 9050

```

sudo netstat -anlp | grep polipo

```

---

### Post by Jabrick on 2011-07-04
> **Dangertux said:**
> Try verifying that polipo is running and bound properly. Check netstat by default it should bind to port 9050

```

sudo netstat -anlp | grep polipo

```

This is my output
```

tcp        0      0 127.0.0.1:8123          0.0.0.0:*               LISTEN      845/polipo    

```

Thank you for continuing to help me out btw.
And I'm using tor button 1.4.0

---

### Post by Dangertux on 2011-07-04
> **Jabrick said:**
> This is my output
```

tcp        0      0 127.0.0.1:8123          0.0.0.0:*               LISTEN      845/polipo    

```Thank you for continuing to help me out btw.
And I'm using tor button 1.4.0

try restarting polipo 

```

sudo /etc/init.d/polipo restart

```Are you using the little TOR addon for firefox? EDIT : NVM I see you said it in your above post.

---

### Post by Jabrick on 2011-07-04
> **Dangertux said:**
> try restarting polipo 

```

sudo /etc/init.d/polipo restart

```Are you using the little TOR addon for firefox? EDIT : NVM I see you said it in your above post.

Yes I have been restarting tor and polipo many time T__T.
I just restarted polipo again and it still isn't working.
And yeah TOR button, suggested by the Tor devs for firefox.
It makes no sense :(
Thank you again for continueing to help, means so much right now.
ARGH!!

EDIT: Do you know if I can change how long I have to connect to a website before firefox determines it too long?
      Could it be that tor network is just acting up really slow? But from my experience from privoxy before moving to polipo I feel like thats not the case. Plus I've been at this for a while now.

---

### Post by Dangertux on 2011-07-04
> **Jabrick said:**
> Yes I have been restarting tor and polipo many time T__T.
I just restarted polipo again and it still isn't working.
And yeah TOR button, suggested by the Tor devs for firefox.
It makes no sense :(
Thank you again for continueing to help, means so much right now.
ARGH!!

Give me a minute I'm installing  tor/polipo on this machine and using the config you are to see if I can see the problem better. Will reply in a minute.

---

### Post by Jabrick on 2011-07-04
> **dangertux said:**
> give me a minute i'm installing  tor/polipo on this machine and using the config you are to see if i can see the problem better. Will reply in a minute.

thank you so much!
UPDATE: I dont know if its important but I'm on arch using the polipo-git, because the one provided by pacman wouldn't work properly. It was suggested by another user from arch that i should use the polipo-git. Which it did work for a while, but then stopped....

---

### Post by Dangertux on 2011-07-04
OK -- This is what I want you to try 

```

sudo nano /etc/polipo/config

```

Inside you will see two lines

```

proxyAddress = "127.0.0.1"
proxyPort = 8118

```

Now I have a sneaking suspicion your proxyPort might say something else, try changing it to 8118 then do the following.

```

sudo /etc/init.d/polipo restart && sudo /etc/init.d/tor restart

```

Then re-enable Tor button and see if that works for you.

---

### Post by Jabrick on 2011-07-05
Sorry I ended up falling asleep, anyways here is my config, I got this from tor.
[https://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf](https://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf)
```


### Basic configuration
### *******************

# Uncomment one of these if you want to allow remote clients to
# connect:

# proxyAddress = "::0"        # both IPv4 and IPv6
# proxyAddress = "0.0.0.0"    # IPv4 only

proxyAddress = "127.0.0.1"
proxyPort = 8118

# If you do that, you'll want to restrict the set of hosts allowed to
# connect:

# allowedClients = "127.0.0.1, 134.157.168.57"
# allowedClients = "127.0.0.1, 134.157.168.0/24"

allowedClients = 127.0.0.1
allowedPorts = 1-65535

# Uncomment this if you want your Polipo to identify itself by
# something else than the host name:

proxyName = "localhost"

# Uncomment this if there's only one user using this instance of Polipo:

cacheIsShared = false

# Uncomment this if you want to use a parent proxy:

# parentProxy = "squid.example.org:3128"

# Uncomment this if you want to use a parent SOCKS proxy:

socksParentProxy = "localhost:9050"
socksProxyType = socks5


### Memory
### ******

# Uncomment this if you want Polipo to use a ridiculously small amount
# of memory (a hundred C-64 worth or so):

# chunkHighMark = 819200
# objectHighMark = 128

# Uncomment this if you've got plenty of memory:

# chunkHighMark = 50331648
# objectHighMark = 16384

chunkHighMark = 67108864

### On-disk data
### ************

# Uncomment this if you want to disable the on-disk cache:

diskCacheRoot = ""

# Uncomment this if you want to put the on-disk cache in a
# non-standard location:

# diskCacheRoot = "~/.polipo-cache/"

# Uncomment this if you want to disable the local web server:

localDocumentRoot = ""

# Uncomment this if you want to enable the pages under /polipo/index?
# and /polipo/servers?.  This is a serious privacy leak if your proxy
# is shared.

# disableIndexing = false
# disableServersList = false

disableLocalInterface = true
disableConfiguration = true

### Domain Name System
### ******************

# Uncomment this if you want to contact IPv4 hosts only (and make DNS
# queries somewhat faster):
#
# dnsQueryIPv6 = no

# Uncomment this if you want Polipo to prefer IPv4 to IPv6 for
# double-stack hosts:
#
# dnsQueryIPv6 = reluctantly

# Uncomment this to disable Polipo's DNS resolver and use the system's
# default resolver instead.  If you do that, Polipo will freeze during
# every DNS query:

dnsUseGethostbyname = yes


### HTTP
### ****

# Uncomment this if you want to enable detection of proxy loops.
# This will cause your hostname (or whatever you put into proxyName
# above) to be included in every request:

disableVia = true

# Uncomment this if you want to slightly reduce the amount of
# information that you leak about yourself:

# censoredHeaders = from, accept-language
# censorReferer = maybe

censoredHeaders = from,accept-language,x-pad,link
censorReferer = maybe

# Uncomment this if you're paranoid.  This will break a lot of sites,
# though:

# censoredHeaders = set-cookie, cookie, cookie2, from, accept-language
# censorReferer = true

# Uncomment this if you want to use Poor Man's Multiplexing; increase
# the sizes if you're on a fast line.  They should each amount to a few
# seconds' worth of transfer; if pmmSize is small, you'll want
# pmmFirstSize to be larger.

# Note that PMM is somewhat unreliable.

# pmmFirstSize = 16384
# pmmSize = 8192

# Uncomment this if your user-agent does something reasonable with
# Warning headers (most don't):

# relaxTransparency = maybe

# Uncomment this if you never want to revalidate instances for which
# data is available (this is not a good idea):

# relaxTransparency = yes

# Uncomment this if you have no network:

# proxyOffline = yes

# Uncomment this if you want to avoid revalidating instances with a
# Vary header (this is not a good idea):

# mindlesslyCacheVary = true

# Suggestions from Incognito configuration
maxConnectionAge = 5m
maxConnectionRequests = 120
serverMaxSlots = 8
serverSlots = 2
tunnelAllowedPorts = 1-65535

```
And now fiefox says proxy server is refusing connections.
I'll be back on the forums in some hours.
Ugh.

---

### Post by Dangertux on 2011-07-05
:o> **Jabrick said:**
> Sorry I ended up falling asleep, anyways here is my config, I got this from tor.
[https://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf](https://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf)
```


### Basic configuration
### *******************

# Uncomment one of these if you want to allow remote clients to
# connect:

# proxyAddress = "::0"        # both IPv4 and IPv6
# proxyAddress = "0.0.0.0"    # IPv4 only

proxyAddress = "127.0.0.1"
proxyPort = 8118

# If you do that, you'll want to restrict the set of hosts allowed to
# connect:

# allowedClients = "127.0.0.1, 134.157.168.57"
# allowedClients = "127.0.0.1, 134.157.168.0/24"

allowedClients = 127.0.0.1
allowedPorts = 1-65535

# Uncomment this if you want your Polipo to identify itself by
# something else than the host name:

proxyName = "localhost"

# Uncomment this if there's only one user using this instance of Polipo:

cacheIsShared = false

# Uncomment this if you want to use a parent proxy:

# parentProxy = "squid.example.org:3128"

# Uncomment this if you want to use a parent SOCKS proxy:

socksParentProxy = "localhost:9050"
socksProxyType = socks5


### Memory
### ******

# Uncomment this if you want Polipo to use a ridiculously small amount
# of memory (a hundred C-64 worth or so):

# chunkHighMark = 819200
# objectHighMark = 128

# Uncomment this if you've got plenty of memory:

# chunkHighMark = 50331648
# objectHighMark = 16384

chunkHighMark = 67108864

### On-disk data
### ************

# Uncomment this if you want to disable the on-disk cache:

diskCacheRoot = ""

# Uncomment this if you want to put the on-disk cache in a
# non-standard location:

# diskCacheRoot = "~/.polipo-cache/"

# Uncomment this if you want to disable the local web server:

localDocumentRoot = ""

# Uncomment this if you want to enable the pages under /polipo/index?
# and /polipo/servers?.  This is a serious privacy leak if your proxy
# is shared.

# disableIndexing = false
# disableServersList = false

disableLocalInterface = true
disableConfiguration = true

### Domain Name System
### ******************

# Uncomment this if you want to contact IPv4 hosts only (and make DNS
# queries somewhat faster):
#
# dnsQueryIPv6 = no

# Uncomment this if you want Polipo to prefer IPv4 to IPv6 for
# double-stack hosts:
#
# dnsQueryIPv6 = reluctantly

# Uncomment this to disable Polipo's DNS resolver and use the system's
# default resolver instead.  If you do that, Polipo will freeze during
# every DNS query:

dnsUseGethostbyname = yes


### HTTP
### ****

# Uncomment this if you want to enable detection of proxy loops.
# This will cause your hostname (or whatever you put into proxyName
# above) to be included in every request:

disableVia = true

# Uncomment this if you want to slightly reduce the amount of
# information that you leak about yourself:

# censoredHeaders = from, accept-language
# censorReferer = maybe

censoredHeaders = from,accept-language,x-pad,link
censorReferer = maybe

# Uncomment this if you're paranoid.  This will break a lot of sites,
# though:

# censoredHeaders = set-cookie, cookie, cookie2, from, accept-language
# censorReferer = true

# Uncomment this if you want to use Poor Man's Multiplexing; increase
# the sizes if you're on a fast line.  They should each amount to a few
# seconds' worth of transfer; if pmmSize is small, you'll want
# pmmFirstSize to be larger.

# Note that PMM is somewhat unreliable.

# pmmFirstSize = 16384
# pmmSize = 8192

# Uncomment this if your user-agent does something reasonable with
# Warning headers (most don't):

# relaxTransparency = maybe

# Uncomment this if you never want to revalidate instances for which
# data is available (this is not a good idea):

# relaxTransparency = yes

# Uncomment this if you have no network:

# proxyOffline = yes

# Uncomment this if you want to avoid revalidating instances with a
# Vary header (this is not a good idea):

# mindlesslyCacheVary = true

# Suggestions from Incognito configuration
maxConnectionAge = 5m
maxConnectionRequests = 120
serverMaxSlots = 8
serverSlots = 2
tunnelAllowedPorts = 1-65535

```And now fiefox says proxy server is refusing connections.
I'll be back on the forums in some hours.
Ugh.

Ok I think I know what the problem is ; if this is your config file -- and the above was your netstat output. This is not the config file being used...

So this is what you should try. 

```

sudo mv /etc/polipo/config /etc/polipo/config.old
sudo touch /etc/polipo/config
sudo nano /etc/polipo/config

```Then paste EXACTLY what you posted above in the file hit ctrl+s to save and ctrl+x to exit. Then restart polipo and tor as mentioned above, I think this should work for you.

Btw sorry I also fell asleep and ended up having to work early lol :-P

---

### Post by Jabrick on 2011-07-05
Ok I did what you told me and now
sudo netstat -anlp | grep polipo
outputs
```

tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN      820/polipo          
tcp        1      0 127.0.0.1:8118          127.0.0.1:45022         CLOSE_WAIT  820/polipo          
tcp        0      0 127.0.0.1:46148         127.0.0.1:9050          ESTABLISHED 820/polipo

```
Progress?
Anyways i restarted my daemons and my computer too, it still isn't working? Could it be a problem in tor?
I swear it shouldn't be this difficult, because it was working at the beginning and then just stopped. How is this possible?!?!
By the way sir, you are the BEST! :)

---

### Post by Dangertux on 2011-07-05
> **Jabrick said:**
> Ok I did what you told me and now
sudo netstat -anlp | grep polipo
outputs
```

tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN      820/polipo          
tcp        1      0 127.0.0.1:8118          127.0.0.1:45022         CLOSE_WAIT  820/polipo          
tcp        0      0 127.0.0.1:46148         127.0.0.1:9050          ESTABLISHED 820/polipo

```Progress?
Anyways i restarted my daemons and my computer too, it still isn't working? Could it be a problem in tor?
I swear it shouldn't be this difficult, because it was working at the beginning and then just stopped. How is this possible?!?!
By the way sir, you are the BEST! :)

Well I appreciate the vote of confidence -- It could quite possibly be a problem with Tor. I am fairly happy with how your polipo is looking at this moment. So let's hop over and do a netstat like this

```

sudo netstat -anlp | grep tor

```

If that looks good the other thing you can try is checking your Tor button settings. They should look like the attached screen shot. Make sure that the host is 127.0.0.1 and the port is 8118 if it's not change it, but it should be. You can test your settings to and see if that works.

---

### Post by Jabrick on 2011-07-05
The ouput from sudo netstat -anlp | grep tor
```

tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      986/tor             
tcp        0      0 192.168.0.193:36055     217.115.137.222:443     ESTABLISHED 986/tor             
unix  2      [ ]         DGRAM                    11161  986/tor             
unix  3      [ ]         STREAM     CONNECTED     4754   986/tor             
unix  3      [ ]         STREAM     CONNECTED     4753   986/tor

```
Also in the tor setting when I click use recommended settings, the Polipo box isn't checked. I cannot get it to be checked, its greyed out. I wish I could rep you or something.
I tried using custom settings and adding in the appropriate values, but that doesn't seem to work.

---

### Post by Dangertux on 2011-07-05
> **Jabrick said:**
> The ouput from sudo netstat -anlp | grep tor
```

tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      986/tor             
tcp        0      0 192.168.0.193:36055     217.115.137.222:443     ESTABLISHED 986/tor             
unix  2      [ ]         DGRAM                    11161  986/tor             
unix  3      [ ]         STREAM     CONNECTED     4754   986/tor             
unix  3      [ ]         STREAM     CONNECTED     4753   986/tor

```Also in the tor setting when I click use recommended settings, the Polipo box isn't checked. I cannot get it to be checked, its greyed out. I wish I could rep you or something.
I tried using custom settings and adding in the appropriate values, but that doesn't seem to work.

LOL -- I wish I could rep me too , J/K ;-)

OK -- so we now know that your Tor button appears to not be working right. Let's try 2 things, first we're going to try to "Restore Defaults" for Tor Button, if that doesn't work. We can try reinstalling the Tor Button

In firefox go to tools > addons 

Then choose Uninstall for Tor Button.  After that try downloading installing Tor Button from this source

[https://addons.mozilla.org/en-US/firefox/addon/torbutton/](https://addons.mozilla.org/en-US/firefox/addon/torbutton/)

That is the one I used so I know it works right -- it will probably want to update after you install it, that is fine. It will restart Firefox as well. So make sure you save any tabs you need when you're done. 

Hopefully that will help you if not post back and we'll see what other voodoo we can conjure up ;-)

---

### Post by Jabrick on 2011-07-06
Ok I'm running firefox 5, and the version of torbutton will not work with my firefox even after overriding the compatibility warnings.
So I re-installed tor button 1.4 multiple times already and still I cannot select the polipo check box.
So tomorrow I will downgrade my firefox, for now I must sleep.
Not enough time during the day :(
Anyways thanks a bunch again, I will get back to you! :)

---

### Post by Dangertux on 2011-07-06
> **Jabrick said:**
> Ok I'm running firefox 5, and the version of torbutton will not work with my firefox even after overriding the compatibility warnings.
So I re-installed tor button 1.4 multiple times already and still I cannot select the polipo check box.
So tomorrow I will downgrade my firefox, for now I must sleep.
Not enough time during the day :(
Anyways thanks a bunch again, I will get back to you! :)

No problem for the help -- Firefox 5 may be the issue (I haven't tried it yet)

If that still doesn't work you can try manually setting your firefox settings without the Tor button it should still work. You just won't be able to disable and enable tor with a click.

your proxy settings would obviously still be 127.0.0.1 port 8118

---

### Post by Jabrick on 2011-07-06
Hey I tried using manual configuration and just my luck it doesn't work, I've been trying different settings, along with conjuction with tor button and I found this while loading.

XML Parsing Error: no element found
Location: jar:file:///usr/lib/firefox-5.0/omni.jar!/chrome/toolkit/content/global/netError.xhtml
Line Number 1, Column 1:

I dont know if this means anything to you?
Anyways I will ticker around with it later when I have time again, and if everthing fails firefox downgrade :(

---

### Post by Dangertux on 2011-07-06
> **Jabrick said:**
> Hey I tried using manual configuration and just my luck it doesn't work, I've been trying different settings, along with conjuction with tor button and I found this while loading.

XML Parsing Error: no element found
Location: jar:file:///usr/lib/firefox-5.0/omni.jar!/chrome/toolkit/content/global/netError.xhtml
Line Number 1, Column 1:

I dont know if this means anything to you?
Anyways I will ticker around with it later when I have time again, and if everthing fails firefox downgrade :(

Not positive but I think that is in regard to FireFox sync'ing with other Browsers not positive though, but I don't think it effects the current issue.

---

### Post by Jabrick on 2011-07-07
Solved Finally!
Dangertux Thank you for your awesome support!
I was using vidalia and realized in the logs that my system clock was off.
So for me I had to run the command
pacman -Sy ntp && ntpdate pool.ntp.org as root to restore my system clock. (This is for arch linux)
And now it works even though I still can't check off the polipo box!
YES!!! I was at this for maybe three days or so!!!
I AM HAPPY.
THANKS AGAIN SIR!
You are truly a great person of the linux community! :)

P.S: Now how do I mark this as SOLVED? haha I tried editing the first post...

---

