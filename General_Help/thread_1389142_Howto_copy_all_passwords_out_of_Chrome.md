---
title: "Howto copy all passwords out of Chrome?"
date: 2010-01-24
forum: General Help
---

### Post by last1 on 2010-01-24
I need to generate a list of all the passwords I have stored inside of Chrome's password manager. I don't know how to do this though, since they are encrypted inside of a database. The only option seems to be Show Passwords from inside of options, which is ridiculous because I would have to show each password for each site, one by one. That is tedious. 

I'm sure nobody has any solution, but maybe some day a couple years from now someone will respond to this with an answer, and I will have a better way of doing it. Looking forward to that day. Cheers.

---

### Post by lovinglinux on 2010-01-24
> **last1 said:**
> I'm sure nobody has any solution, but maybe some day a couple years from now someone will respond to this with an answer, and I will have a better way of doing it. Looking forward to that day. Cheers.

Lass than an hour is good for you? :)

I don't know why some people love Chrome so much. OK, it is fast, but that is not enough. Because of situations like this that I always say, nothing beats Firefox (yet). I'm currently using [KDE Wallet password integration](https://addons.mozilla.org/en-US/firefox/addon/49357) extension ([there is a Gnome version too](https://addons.mozilla.org/en-US/firefox/addon/8737)), so all Firefox passwords are stored in Kwallet. Nevertheless, Firefox password manager is pretty decent and there are several extensions to enhance it.

Well, enough of Chrome bashing...

I don't think there is a clean method of doing that. I have searched Chrome extension database and could find anything remotely similar to what you need. Nevertheless, I can suggest a very dirty trick:

1) Install Chrome for Windows using Wine
2) Install [url=http://lastpass.com/
]Lastpass[/url] for Windows
3) Copy your password database from the Linux Chrome to the Windows Chrome
4) Upload your passwords to Lastpass and use it to export the passwords
5) You could also install [lastpass](https://addons.mozilla.org/en-US/firefox/addon/8542) for Firefox and import those passwords there if the export functions of Lastpass doesn't meet your requirements. Then you can export them using [Password Exporter](https://addons.mozilla.org/en-US/firefox/addon/2848).

You could also try XMarks, but I'm not sure the password sync is available for Chrome.

Good luck.

BTW, whatever browser I'm using, I also save every new password I create on KeePassX.

---

### Post by last1 on 2010-01-24
Well, that's a clever idea. Did you just figure that out, or is there a walkthrough somewhere that shows how to do things like copy the password databases.

---

### Post by lovinglinux on 2010-01-24
> **last1 said:**
> Well, that's a clever idea. Did you just figure that out, or is there a walkthrough somewhere that shows how to do things like copy the password databases.

I figured it out and haven't tested it. So, there isn't any step-by-step explanation.

---

### Post by last1 on 2010-01-25
Interesting. I ended up just doing it manually actually before I even knew you replied, but the next time I switch to a new OS I may just try this.

---

