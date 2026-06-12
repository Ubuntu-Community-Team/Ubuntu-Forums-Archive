---
title: "Chrome won't let gedit use html extension..."
date: 2011-08-17
forum: General Help
---

### Post by Simeo on 2011-08-17
Ok, this is really frustrating.

All was well and I was able to work on my clients files through filezilla -> Rightclick the file -> View/Edit -> html file opens in gedit

Then I install Chrome.

Now whenever I try to 'view/edit' the file, instead of opening in gedit it opens in Chrome... EVEN AFTER changing the file association to gedit. When I reboot the computer it then changes the file association back to "Chrome". This is annoying... it's like chrome couldn't possibly imagine I would want to use a program other than chrome!

Please help...

---

### Post by tredegar on 2011-08-17
R-click the file
Open with .... **gedit**
Works for me (10.04, gnome)

---

### Post by Simeo on 2011-08-17
> **tredegar said:**
> R-click the file
Open with .... **gedit**
Works for me (10.04, gnome)

Yea, it works that way outside of filezilla. I'm talking about within filezilla. 

There is no "Open with" option in filezilla.

---

### Post by tredegar on 2011-08-17
As I understand it **chrome** is a google-funded application, and closed source. As such, I do not run it. It might be full of nasty stuff, that they will not let me learn about.

**chromium** is an open-source application, I trust it better, and have run it.

I have never used filezilla (an **ftp** or **sftp** client?), but I think **nautilus** can provide all the functionality you need, once you have configured it. I use, in nautilus:

```

sftp://username@hostname/home/username
```
all the time. Once you have set up **ssh**, confirmed and accepted the new remote host's identity, it "just works". Drag, drop, open or edit. All securely with clicky-clicky sweetness. Authentication is handled by the public / private keys.

You should set up **ssh** to do public/private key authentication, then you do not have to use passwords (and, indeed, should disable this method of authentication, because it is open to brute force attack [guessing names & passwords]). 

I suggest you try this.

Linux already has the tools you need to achieve what you want. You just need to learn which tools to use and how to use them to your convenience and satisfaction.

Post back if you get stuck.

---

### Post by Simeo on 2011-08-17
> **tredegar said:**
> As I understand it **chrome** is a google-funded application, and closed source. As such, I do not run it. It might be full of nasty stuff, that they will not let me learn about.

**chromium** is an open-source application, I trust it better, and have run it.

I feel most comfortable working with filezilla for my ftp work. I'm not feeling like learning a new software quite yet, but maybe someday. ;)

I too am an advocate for open-source software over closed... but what's the difference between Chrome and Chromium (really what's the difference)?

---

### Post by tredegar on 2011-08-18
> I'm not feeling like learning a new software quite yet, but maybe someday.
It is hardly "new software" - **nautilus** is otherwise known as your "file browser", it's what you use to navigate your local filesystem, but it will also connect to remote servers with sftp if you put
**sftp://username@server/path/to/directory/** into the location bar.

> what's the difference between Chrome and Chromium?
Here's one explanation: [http://code.google.com/p/chromium/wiki/ChromiumBrowserVsGoogleChrome](http://code.google.com/p/chromium/wiki/ChromiumBrowserVsGoogleChrome)

---

### Post by Simeo on 2011-08-18
> **tredegar said:**
> It is hardly "new software" - **nautilus** is otherwise known as your "file browser", it's what you use to navigate your local filesystem, but it will also connect to remote servers with sftp if you put
**sftp://username@server/path/to/directory/** into the location bar.

Oh that's good... it's like... it's pretty good... thank you.

> 
Here's one explanation: [http://code.google.com/p/chromium/wiki/ChromiumBrowserVsGoogleChrome](http://code.google.com/p/chromium/wiki/ChromiumBrowserVsGoogleChrome)

Thank you. So essentially... there is no real difference?

---

