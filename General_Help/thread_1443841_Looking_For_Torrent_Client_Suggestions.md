---
title: "Looking For Torrent Client Suggestions"
date: 2010-03-31
forum: General Help
---

### Post by ryokea on 2010-03-31
Currently running v1.1.9 of Deluge because it has the two things I need from a torrent client: RSS downloader and a web interface. As of an hour ago it has started to exhibit some strange behavior, the download speed is listed as a very large negative number and it will only download in short bursts.

So far a reinstall and deleting the configuration files have not fixed this little issue and in fact has rendered it unusable due to locking up at start. Without an RSS solution for the latest version of Deluge I am reluctant to upgrade.

I am open to suggestions of alternate clients, and at this point willing to do without a web interface so long as I can get a working RSS downloader running.

---

### Post by francescogondolin on 2010-03-31
I use Ktorrent, works perfectly

---

### Post by Azabith on 2010-03-31
You might want to look into Vuze

---

### Post by wojox on 2010-03-31
I recently tried miro and liked it. Had been using Deluge. Try here to optimize it: [BitTorrent optimization and troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=1259923")

---

### Post by ryokea on 2010-03-31
I've used Ktorrent and Vuze in the past. Both worked very well. If I remember correctly, I stopped using Vuze due to it not liking my setup at all. I believe the only reason I stopped using Ktorrent is because I managed to get Deluge's RSS plugin working. May end up going back to Ktorrent.

---

### Post by Cas07 on 2010-04-01
Why dont you use Deluge 1.2.2 that is in [PPA]("https://launchpad.net/~deluge-team/+archive/ppa?field.series_filter=karmic") and use FlexGet for the RSS Feed.

---

### Post by doas777 on 2010-04-01
joc, was that large negative number -2147483648?

I have used azureus/vuze, but i am looking into torrentflux now. I'm looking for somthing that uses a web interface.

---

### Post by ryokea on 2010-04-01
> **doas777 said:**
> joc, was that large negative number -2147483648?

I have used azureus/vuze, but i am looking into torrentflux now. I'm looking for somthing that uses a web interface.

It was different every time, and actually changed here and there while running. I liked my old setup with Deluge, had a script to run it all and start the WebUI so if I can get it to work again that would be nice.

---

### Post by KayakJim on 2010-04-01
Have you tried purging the deluge installation and then reinstalling?

I know you said you had deleted some of the configuration files but did you do:
```
sudo aptitude purge deluge
```

---

### Post by NCLI on 2010-04-01
First do:
```
sudo aptitude purge deluge
```

then:
> **Caos said:**
> Why dont you use Deluge 1.2.2 that is in [PPA]("https://launchpad.net/~deluge-team/+archive/ppa?field.series_filter=karmic") and use FlexGet for the RSS Feed.

and finally:

```
sudo apt-get install deluge
```

---

### Post by ryokea on 2010-04-01
The purge command didn't fix the issue with that version, but since I had Vuze in place I decided to play around with Deluge again. Built it from source and it runs just fine now minus the FlexRSS plugin which isn't compatible with the newest version.

Looks like I get to play around with FlexGet now and set up a cron job for it. Suppose since my issue has been resolved I'll mark this appropriately.

---

### Post by KayakJim on 2010-04-01
Vuze is so bloated. 

I would use Transmission instead if Deluge didn't do it for you.

---

### Post by ryokea on 2010-04-01
> **KayakJim said:**
> Vuze is so bloated. 

I would use Transmission instead if Deluge didn't do it for you.

Vuze actually was starting to get on my nerves because it took so long to shutdown fully. I eventually wrote a custom script that would check for a few things to see if Vuze was running and if so, kill the java process. Yes I realize that isn't a recommended solution at all but it worked for my purposes.

I like Transmission, and used to use it until I decided to try new things. Right now Deluge seems to be working just fine for me and I'll just get used to using FlexGet to grab torrent files so I can use that as a universal implementation since most clients have the watch folder option.

---

