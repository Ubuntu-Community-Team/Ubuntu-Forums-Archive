---
title: "Google Chrome Repositories?"
date: 2010-02-26
forum: General Help
---

### Post by uRock on 2010-02-26
Am I the only one having a problem doing updates because of Google's repository being down?

---

### Post by uRock on 2010-02-26
```
ping 192.168.1.9
```

---

### Post by sports fan Matt on 2010-02-26
Mine won't update either..same repo.

---

### Post by fragos on 2010-02-27
That repo is certainly up now. What was "ping 192.168.1.9" for? It's a local NAT address that would have nothing to do with Google or any other site on the Internet.

---

### Post by uRock on 2010-02-27
> **fragos said:**
> That repo is certainly up now. What was "ping 192.168.1.9" for? It's a local NAT address that would have nothing to do with Google or any other site on the Internet.

Just an odd way of bumping a thread. Nothing more.

---

### Post by uRock on 2010-02-27
Nope, it is still down. Or some how they up and changed something without adding it to an update first.

---

### Post by DoeRayMe on 2010-02-27
Down for me too :(

---

### Post by uRock on 2010-02-28
I keep re-enabling it every day or so to see if it will update, but nope.

If anyone is connecting, please let the rest of us know which repo you are using.

Thanx,
Ronnie

---

### Post by fragos on 2010-02-28
URI: [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/)
Distribution: stable
components: main

---

### Post by uRock on 2010-03-01
So, what has happened to make this repo not work for some and be problemless for others? I have 4 machines that I have had to disable the Google repo just to do updates.

---

### Post by uRock on 2010-03-04
I am still having problems with this. It has been almost two weeks since I had to remove the google line from the sources app and every time I add it back, it gives the same error I listed in the first post. I am sure that by now I am missing a security update or two from the Google repo.

Thanx,
Ronnie

---

### Post by uRock on 2010-03-04
I just tried uninstalling it. Everything uninstalled to include all entries in the sources list.

I then downloaded and reinstalled Chrome and tried running updates. Yet again I had the same problem listed in the first post.

---

### Post by fragos on 2010-03-04
For what it's worth, I used Ubuntu Tweak to add the Google repository and also to select Chrome for installation. I don't know what that does differently but I've never had your problem.

---

### Post by Jonah Bron on 2010-03-04
I have Chromium, and it's at [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu)

---

### Post by uRock on 2010-03-04
> **fragos said:**
> For what it's worth, I used Ubuntu Tweak to add the Google repository and also to select Chrome for installation. I don't know what that does differently but I've never had your problem.

I'll give that a try. I find this issue really odd. Especially being you and I are probably hitting the same servers for updates in this part of the country.

---

### Post by uRock on 2010-03-04
> **fragos said:**
> For what it's worth, I used Ubuntu Tweak to add the Google repository and also to select Chrome for installation. I don't know what that does differently but I've never had your problem.

I added the source on their site for Chrome and it fixed it. Very odd, but it helped. Thanx.

```
deb http://dl.google.com/linux/deb/ stable non-free main
```

---

### Post by uRock on 2010-03-04
The original entry in the source list did not have *non-free* in it.

---

### Post by uRock on 2010-03-05
Of coarse it has started taking forever again.

---

### Post by fragos on 2010-03-05
Perhaps which mirror you are using is part of the problem. Open Software Sources and click on the download source, select Other and then the "Select Best Server" button. It picked [http://mirrors.us.kernel.org/ubuntu](http://mirrors.us.kernel.org/ubuntu) for me. If you get an odd result do it again. I believe it test mirror response time to your location and picks the quickest when the tests were run.

---

### Post by uRock on 2010-03-06
I tried a few of them to include the one you have and the reload/update still hangs on the google server. After a minute or two it finally finishes.

---

### Post by deadlockedgamer on 2010-03-06
I have the google repo. I do not get all servers touched unless I refresh the update check a few times in ubuntu tweak. However I suspect the get deb repos I have somehow effect this. However it is not down it just seems to time out way too fast!

---

### Post by uRock on 2010-03-22
ip route 0.0.0.0 255.255.255.0 s0/1
no shut
exit

---

