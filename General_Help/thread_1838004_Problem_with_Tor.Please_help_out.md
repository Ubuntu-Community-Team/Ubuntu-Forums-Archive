---
title: "Problem with Tor.Please help out??"
date: 2011-09-02
forum: General Help
---

### Post by knight30 on 2011-09-02
Hi guys 

I just was looking for good programs to hide my ip and i got this popular program Tor,everyone know it.Any way, I've downloaded and installed the program but when i ran the program it's stuck and cant continue .It actually reach with "establishing an encrypted directory connection" and then the bar stop at that spot plz help me out???
i have pictured that problem in the attachment..

---

### Post by knight30 on 2011-09-02
please guys help me with this problem 

anyone knows what's the problem and why happen to me????

---

### Post by Pakia on 2011-09-04
Ensure you are using privoxy or polipo. Polipo seems to work out of the box which you should add the line (forward-socks5 / 127.0.0.1:9050 .) to the top of your privoxy.conf file. In your torrc file add the following to speed up connections;

# Set the Tor Circuit Build time to find faster tor servers, increments of seconds
CircuitBuildTimeout 2
# connections while Tor is not in use.
KeepalivePeriod 60
# Force Tor to consider whether to build a new circuit every NUM seconds.
NewCircuitPeriod 15
# Set How many entry guards we should keep at a time
NumEntryGuards 8

To be able to browse google safely without cookies do the following;

Switch off your proxy
Activate cookies
Go to [https://encrypted.google.com?.jpg/speed/public-dns/index.html](https://encrypted.google.com?.jpg/speed/public-dns/index.html)
Hit search without entering anything in the search bar
Then go to the advanced search
Once again do a search without anything in the bar 
Bookmark this page
Deactivate cookies
Close browser
Activate proxy
Open browser and google works in the Tor net without cookies.

Your can also consider using the ttdns for tor dns. 
I changed the standard dns 8.8.8.8 (google) to 208.67.220.220 and 208.67.222.222 (open dns) which seems to be faster.

Good luck

---

### Post by Pakia on 2011-09-04
I forgot - ensure your system clock is correct according to your region. If it is to far out the network will not log you in

---

### Post by knight30 on 2011-09-08
Thanx dude but really i didnt get you ??

i meant what exactly i have to do to make it work???

and why this problem happen 

is it my ISP blocking the program ??or what??

---

### Post by meborc on 2011-09-12
you can easily try tor WITHOUT doing any installations or configurations

go to [https://www.torproject.org/download/download-easy.html.en](https://www.torproject.org/download/download-easy.html.en)

download tor browser bundle (it includes interner browser and configurations needed for tor)

1) extract
2) run

simple as that

If you need tor to work with other programs, i suggest you read the documentation

---

