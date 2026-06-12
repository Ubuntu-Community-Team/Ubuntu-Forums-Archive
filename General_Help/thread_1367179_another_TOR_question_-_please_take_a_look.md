---
title: "another TOR question - please take a look"
date: 2009-12-29
forum: General Help
---

### Post by Nailox on 2009-12-29
I tried using torproject.org docs - no luck - error with the gpg line in the source.list
I tried this manual:
> Google is your friend:

[http://blog.aizatto.com/2006/09/01/p...-dapper-drake/]("http://blog.aizatto.com/2006/09/01/protecting-your-privacy-setting-up-tor-in-ubuntu-dapper-drake/")

   1. Run the command: sudo apt-get install tor privoxy
   2. Run the command: sudo gedit /etc/privoxy/config
   3. Add the line (including the period at the end): forward-socks4a / localhost:9050 .
   4. Comment out the line: logfile logfile
   5. Comment out the line: jarfile jarfile
   6. Restart the Privoxy service: sudo /etc/init.d/privoxy restart

How to set up Firefox to work with Tor:

   1. Install the torbutton extension.
   2. Restart Firefox
   3. In the bottom right corner you’ll have a text blurb saying: Tor Disabled
   4. Enable Tor by clicking the blurb; it should say: Tor Enabled
   5. Surf the web

(Note: I'm using Tor on Fiesty, using the above steps and all works well...as a final step, check your IP with Tor button off, turn it on and refresh...if the numbers are different, you're gold.) :wink: 

and i get this in terminal:
> sudo apt-get install tor privoxy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tor has no installation candidate 

Im running out of patience.. I know this is karmic stuff  and we have to suffer but common...

---

### Post by 3rdalbum on 2009-12-29
It looks like Tor has been removed from Karmic. You probably need to use a third party repository or a PPA to install Tor.

This "GPG error in the sources.list" - there shouldn't be anything to do with GPG in the sources.list. In fact, you shouldn't be editing sources.list manually, you should use System > Administration > Software Sources instead.

To set up Tor, go to System > Administration > Software Sources. Go to the "Third party software" tab. Click the Add button, and paste in the following:

```
deb http://deb.torproject.org/torproject.org karmic main
```

Click the "Add Source" button, then click Close. You'll be asked if you want to update your package list - don't just yet.

Open up a terminal and paste in the following three commands individually:

```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
sudo apt-get update
```

After that, tor and tor-geoipdb will be installable.

And you can continue your instructions.

(NOTE: If it complains about an error in the sources.list, then open up that file and remove anything that doesn't begin with 'deb', 'deb-src' or the hash symbol # ).

---

### Post by Nailox on 2009-12-30
i solved the problem by moving to Germany.. see : > IP Address Location: Erfurt, Thuringen Germany  [IMG]http://whatismyipaddress.com/images/flags/de.png[/IMG] :KS

thanks 3rdalbum !

---

