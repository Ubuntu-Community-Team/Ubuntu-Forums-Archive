---
title: "why clicking hyperlink twice speeds up page load"
date: 2012-03-11
forum: General Help
---

### Post by MichaelBurns on 2012-03-11
I run Lucid Live on a netbook.  I use the standard Firefox web browser.

Very often, when I click a hyperlink, the only thing that happens is that I see the status bar at the bottom right of the browser appear and then just linger at zero progress for up to a minute (if I have the patience).  However, if I just click on the link again instead of waiting, then the page loads within seconds.  Is there a browser setting that will fix this?  (meaning that the page will load within seconds without having to click twice)

---

### Post by lovinglinux on 2012-03-15
Try the Network Tweaks from [http://www.webgapps.org/tutorials/firefox/optimization/preferences-tweaks](http://www.webgapps.org/tutorials/firefox/optimization/preferences-tweaks)

---

### Post by MichaelBurns on 2012-03-21
Thank you for the link, lovinglinux.  I will try those "tweaks" one-at-a-time (which may take me a while).

I still would like to have a better understanding of why I experience the particular single-click vs. double-click load-time problem.

---

### Post by lovinglinux on 2012-03-22
> **MichaelBurns said:**
> Thank you for the link, lovinglinux.  I will try those "tweaks" one-at-a-time (which may take me a while).

I still would like to have a better understanding of why I experience the particular single-click vs. double-click load-time problem.

A web page is a series of web objects, like images, html pages, css style sheets and so on. When you type an url in the address bar, the browser request all that content, which needs to be downloaded to compose the entire page. However, there is a limit of the number of simultaneous connections a browser can make to the site server. So it doesn't download all those files simultaneously. Some of the tweaks I recommended will allow the browser to create more connections and thus download more content files simultaneously. I suppose clicking the link twice could create the same effect, since a new connection will be created.

---

### Post by MichaelBurns on 2012-03-27
Thank you for the explanation, lovinglinux.  I think that makes sense to me.

---

### Post by dcstar on 2012-03-28
> **lovinglinux said:**
> 
..........
I suppose clicking the link twice could create the same effect, since a new connection will be created.

Or you have bad DNS that times out and/or loses the original UDP packet, and a subsequent request for the exact same address gets an immediate response because the DNS server has now had time to get the data.

---

### Post by MichaelBurns on 2012-03-29
Thank you, dcstar.  Unfortunately, I don't understand networking well enough to make use of that information.  (I've never even heard of UDP; thank god Ubuntu is strong in the networking-out-of-the-box department, which is the main reason that I have continued to use Ubuntu despite its other "features".)

BTW, I marked this thread as solved, since my internet connection and browser etc. techincally work, and I now know more after yours and lovinglinux' informative replies.

---

