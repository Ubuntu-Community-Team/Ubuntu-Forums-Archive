---
title: "TOR not working"
date: 2010-10-25
forum: General Help
---

### Post by searchfgold6789 on 2010-10-25
Hi.
Whenever I enable the TOR network in firefox using the torbutton, everything stops working. Clicking on links won't take me to a page. It seems like I cannot navigate to any webpage when TOR is enabled.
When I disable it everything works fine.
Is there a solution for this?

---

### Post by searchfgold6789 on 2010-10-25
bump, sorry.

---

### Post by GlazedWicker on 2010-10-25
You could try restarting the tor daemon.
```
sudo /etc/init.d/tor restart
```

---

### Post by searchfgold6789 on 2010-10-26
restarting the daemon didn't seem to work :(

---

### Post by jim_deadlock on 2010-10-26
You don't mention whether you've had it working previously or not. If not, then I suggest you go to [https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en) and follow their installation instructions to the letter. Note: *"If you're     using Ubuntu, don't use the default packages: use [our deb repository]("https://www.torproject.org/docs/debian.html.en#ubuntu") instead"*.

If you've had it working before and it has suddenly stopped responding out of the blue then you might just be stuck on a bad exit node or something. Install vidalia and try another node. Bear in mind that browsing via the Tor network is usually a lot slower than normal browsing anyway.

if none of this helps, please say whether you immediately get an error message when you try to browse a page, or whether it just takes ages to load. These are different issues.

---

### Post by inameiname on 2010-10-26
How long ago did this start happening? I noticed that the trouble for me started a couple weeks back. I think it has something to do with settings, either that there are new defaults in the most recent version of Tor and you are now required to tweak them manually, OR something else I heard through the grapevine that the newest version of Tor and Polipo are having issues with each other. (If you use Polipo, that is.)

In all, it's got to be one of those things, as I've never had an issue with it for me on several Ubuntu versions, until a few weeks ago.

FYI, this is the message I get if it's enabled:

```

The proxy server is refusing connections
Firefox is configured to use a proxy server that is refusing connections.
    *   Check the proxy settings to make sure that they are correct.

    *   Contact your network administrator to make sure the proxy server is
          working.

```

---

### Post by jim_deadlock on 2010-10-26
I have the latest version (via polipo) on maverick and it's working fine.

Edit: what you have there is a problem with your proxy settings, not Tor itself. Check to make sure polipo is running and also that your browser it set to use proxy localhost:8118

---

### Post by inameiname on 2010-10-26
What might've changed with my proxy settings? I did nothing to change anything, so I'm curious why it would all of a sudden change. I have Googled this issue a lot over the last few weeks, and have noticed many folks have the same issue, many recent, so I sort of figured it was something that was changed, perhaps a default proxy setting that is different than before.

Anyway, how do I check to see if polipo is running and that my browser is set to use proxy localhost:8118? When it was working, I never prior set anything other than installing tor, polipo, and the torbutton in firefox.

---

### Post by searchfgold6789 on 2010-10-26
I have polipo.
Probably.
I installed Tor and it started working, about 4 days ago. I think I saw this issue as soon as i restarted Firefox, but decided to ignore it for a few days.
The exact problem is just as I described. With Tor enabled, I cannot refresh a page, as in it does nothing when I press F5. When I open a link in a new tab, the tab opens up with nothing inside it, and doesn't even try to load. When I just click on links as normal, nothing at all seems to happen.

---

### Post by inameiname on 2010-10-26
What's funny with mine is that while my torbutton is disabled (ie, the icon has the red 'X' on it and I can actually open webpages), when I went to my connection settings under preferences just now, under "Configure Proxies to the Internet", it says I'm set on "Use system proxy settings", and when I click on 'More Information', it says the torbutton is current "ENABLED". Weird.

---

### Post by searchfgold6789 on 2010-10-26
When I try to refresh a page with Tor enabled, I get a screen like the one attached.

---

### Post by jim_deadlock on 2010-10-26
@inameiname try restarting polipo like this:

```
sudo -u proxy service polipo restart
```

I just looked in Firefox to see my proxy settings but the method seems to have changed recently. Here is what I used to do:

Firefox -> Edit -> Preferences -> Advanced -> Network -> Settings

The Firefox addon I use for proxying (Foxyproxy) used to set the manual proxy config to localhost:8118 there, but now it uses system proxy settings. I have no idea where to find that but I'll have a look around and post here if I find it.

To both of you, quite honestly if I were you I would reinstall from scratch using these instructions:

[https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)

---

### Post by inameiname on 2010-10-26
Ok, my issue with Tor has been fixed. I just noticed my version of "/etc/polipo/config" is not the same as the one on the 'torproject' website. It was a while back, but I guess it was updated. It works for me now.

---

### Post by inameiname on 2010-10-26
Thanks for the input, Jim. Seems though that updating my /etc/polipo/config to the latest one on their site fixed things for me. Obviously, using 'torproject's' older version of their tweaked config file messed it all up for me. 

What's interesting on the newest version is that it includes this line, 

proxyPort = 8118

which I believe wasn't in the original. This addition might explain it suddenly working for me, and why using foxyproxy for you and setting it manually works, as it does the same thing. IDK.

Shame this isn't searchfgold6789's problem and solution.

---

### Post by searchfgold6789 on 2010-10-26
restarting polipo ```

sudo -u proxy service polipo restart

```did it for me. Thanks!

---

### Post by inameiname on 2010-10-26
Cool. Glad we both got it solved.

---

### Post by Bleak888 on 2010-12-28
[SIZE=3]Thanks Jim! I was having same issue as inameiname on my recent install of Tor and replacing the polipo config file fixed my issue as well.[/SIZE]

---

### Post by mikodo on 2011-01-12
Hello, 

I just reinstalled Lucid and had the same difficulties. I had to follow your fixes and do both before, I could use tor again.

1. Update my /etc/polipo/config to the latest one from [Polipo     configuration for Tor]("https://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf")   from here: [https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en) then

2. ```
 sudo  - u proxy service polipo restart
```

Then back to tor working again.

Thanks!

---

