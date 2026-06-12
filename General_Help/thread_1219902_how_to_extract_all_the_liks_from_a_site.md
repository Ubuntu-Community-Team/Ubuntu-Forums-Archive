---
title: "how to extract all the liks from a site?"
date: 2009-07-22
forum: General Help
---

### Post by skizofrenito on 2009-07-22
Hello there!

Here comes my first post in the forum! :)

I'm wondering if there is a way to extract/harvest all the links of a site excluding the links that points to other sites? I tried something with wget, but the only I could get was only the links of the homepage.. The same results I had with the lynx..

What I found from google, were solutions that download recursively not only the links, but also the content of the links, something that I don't want.. I want something like an indexer. Only all the links that contains a site.

Please, if someone knows something about that, help me!

Thank you:D

---

### Post by t4thfavor on 2009-07-22
you just want a text file of the link text? 

Like whatever appears between the 

```

<a href= </a>

```

You could probably do this with w3m, and sed or awk, as well as curl. I don't know exactly how you would get there, but its a start.

```

curl --location www.4wd.com|grep "<a href"

```

---

### Post by wojox on 2009-07-22
Yes you must learn regular expressions if you want to scrape pages.

---

### Post by mbeach on 2009-07-22
If you are looking to do this as a programming exercise, then post what you have so far.

If you really just need the links for a one off type situation, I'd download the web developer toolbar for Firefox, then use the Information -> View Link Information option from that toolbar. Is that sort of what you are after?

The web developer toolbar can be found at:
[https://addons.mozilla.org/en-US/firefox/addon/60](https://addons.mozilla.org/en-US/firefox/addon/60)

---

### Post by az on 2009-07-22
~$ apt-cache show httrack
Package: httrack
Priority: optional
Section: universe/web
Installed-Size: 108
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Xavier Roche <roche@httrack.com>
Architecture: i386
Version: 3.43.2-1ubuntu1
Depends: libc6 (>= 2.4), libhttrack2, zlib1g (>= 1:1.1.4)
Suggests: webhttrack, httrack-doc
Filename: pool/universe/h/httrack/httrack_3.43.2-1ubuntu1_i386.deb
Size: 35638
MD5sum: dec63e4869ed5f1ae822c5c69d77293e
SHA1: 00568fb7b6b09566ed1a1f88195ff836d2478ed0
SHA256: 307583eb23bcef9e974414f2a5f8c8d8e845971589fb535fe7821b6106e15f91
Description: Copy websites to your computer (Offline browser)
 HTTrack is an offline browser utility, allowing you to download a World
 Wide website from the Internet to a local directory, building recursively
 all directories, getting html, images, and other files from the server to
 your computer.
 .
 HTTrack arranges the original site's relative link-structure. Simply
 open a page of the "mirrored" website in your browser, and you can
 browse the site from link to link, as if you were viewing it online.
 HTTrack can also update an existing mirrored site, and resume
 interrupted downloads. HTTrack is fully configurable, and has an
 integrated help system.
Homepage: [http://www.httrack.com](http://www.httrack.com)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

---

### Post by mbeach on 2009-07-22
I think the OP is looking for just a list of the links (specifically pointing to a particular domain or relative links only). They are not looking to copy a website locally which I think is what httrack does. Unless of course httrack has an option to simply index all the links without downloading the content - I'm not sure if it does or not.

---

### Post by Choose on 2009-07-22
Hi,if your using firefox,they have an add-on called **Link Gopher** that might be of some use to you
[https://addons.mozilla.org/en-US/firefox/addon/7312]("https://addons.mozilla.org/en-US/firefox/addon/7312")
;)

---

### Post by skizofrenito on 2009-07-23
Thank to all of you for the help.

I tried your suggestions, but I haven't found a solution yet. **Link Gopher **only extract the links of the page, and not from the whole site, like other online link extractors, such as [http://www.iwebtool.com/link_extractor](http://www.iwebtool.com/link_extractor)

I think I have to try more with the **HTTrack**. Seems a very good idea that didn't notice, although I had used it in the past I guess..

Now I try to download the whole site with wget, and process it offline afterwards.. Seems not so good idea, but until now I have not something better to do..

The command with the options that I used is:

wget --recursive --no-clobber --html-extension --convert-links --domains example.com --no-parent --wait=5 --background -e robots=off --user-agent=Firefox [www.example.com](www.example.com)

---

