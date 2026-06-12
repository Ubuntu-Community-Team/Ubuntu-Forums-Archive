---
title: "automation of torrent downloads via email"
date: 2011-04-27
forum: General Help
---

### Post by retano on 2011-04-27
Hi eveyone, 

I have a number of torrents which are updating irregulary (TV shows and such). I also subscribed to the service which notifies me via email when one of them is updated. The thing I would like to achieve is some kind of automation script which will do the following:

1. Upon receive an email with link with updated torrent (not a direct link, it is only link to the page) browser should be opened and *.torrent should be downloaded to the specific folder. 
2. Upon receive an email with random *.torrent file it should be saved to the specific folder.

P.S. I do not want this folder to be shared/accessed from outside of my home network.  

Is this possible?

---

### Post by HermanAB on 2011-04-27
Howdy,

You can make a mail robot using Fetchmail and Procmail.  However, the procmail scripting language is arcane.

---

### Post by retano on 2011-04-29
Looks complex to me (I am a total noob in this), is there an easier way?

---

### Post by SeijiSensei on 2011-04-29
Most BT clients support the use of "RSS" streams.  You can subscribe to a tracker's RSS server and tell the BT client to download the torrents that match a text string, like the show title.  This is a much easier way to monitor releases than the email method you described.

Each client does this differently, but look for something referring to "RSS" or "syndication" in the help documentation.

---

### Post by retano on 2011-05-03
Unfortunately the desired tracker has no RSS feature ...
Update: I found a community project which does RSS for this tracker.  

Now the problem is that my BT client (Transmission) apparently will not work with RSS at all :) Can you recommend a RSS reader which support both cookies and autoloading of .torrent files to the specified folder? Transmission has a watched folder and will pick them up.

---

### Post by retano on 2011-05-04
bump.

---

### Post by retano on 2011-05-11
bump?

---

### Post by MattBD on 2011-05-29
Have you tried Deluge? Apparently that has RSS support via a plugin, and it's a pretty decent BitTorrent client.

---

