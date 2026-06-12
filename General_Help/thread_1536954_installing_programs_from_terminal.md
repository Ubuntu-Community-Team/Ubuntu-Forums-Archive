---
title: "installing programs from terminal"
date: 2010-07-22
forum: General Help
---

### Post by COKEDUDE on 2010-07-22
I've had difficulty installing the program I actually want the last few times I've used my terminal. Here are a few examples. 

I wanted chromium browser so I used this command 
```
sudo apt-get install chromium
```
[http://packages.ubuntu.com/search?keywords=chromium&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=chromium&searchon=names&suite=lucid&section=all)

I wanted epiphany browser so I used this command 
```
sudo apt-get install epiphany
```
[http://packages.ubuntu.com/search?suite=lucid&section=all&arch=any&searchon=names&keywords=epiphany](http://packages.ubuntu.com/search?suite=lucid&section=all&arch=any&searchon=names&keywords=epiphany)

I wanted seamonkey browser so I used this command 
```
sudo apt-get install seamonkey
```
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=SeaMonkey](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=SeaMonkey)

With chromium and epiphany I didn't realize there was a game named chromium and epiphany, so my terminal installed the games instead of the browsers. When I first started using the terminal it told me if there were multiple programs with similar names. So my questions is why is my terminal not telling me that anymore and how do I get my terminal to give me a list of programs with similar names?

Next up seamonkey. How do I get my terminal to list version numbers? My terminal installed a old version of seamonkey :( .

---

### Post by marshmallow1304 on 2010-07-22
You can use
```
apt-cache search <packagename>
```
to find packages matching your query.  It also gives a short description of each package.

The Epiphany Browser is available under the package epiphany-browser.  [s]Chromium is not yet available in the Ubuntu repositories.  You can add the [beta PPA]("https://launchpad.net/~chromium-daily/+archive/beta") if you want it.[/s] EDIT: NVM, it's there now.  It's available under chromium-browser.


To get the version of most installed programs, use
```
<program> --version
```

---

### Post by COKEDUDE on 2010-07-22
This one didn't work :(. 
```
~ $ chromium --version
chromium: command not found
```

---

### Post by ubunterooster on 2010-07-22
May I ask why you want to use the terminal as opposed to synaptic?

---

### Post by watupgroupie on 2010-07-22
For Chromium I think you need the PPA for it. Then it's labeled under Chromium-Browser.

---

### Post by COKEDUDE on 2010-07-23
> **ubunterooster said:**
> May I ask why you want to use the terminal as opposed to synaptic?

I like the terminal :). 

> **watupgroupie said:**
> For Chromium I think you need the PPA for it. Then it's labeled under Chromium-Browser.

Whats PPA?

---

### Post by watupgroupie on 2010-07-23
> **COKEDUDE said:**
> 
Whats PPA?
It's a way for developers to give you updates for programs through the Update Manager. It's especially useful for programs that update frequently. The Chromium PPA is located at [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa) and there's instructions on that page to install it (using the terminal :)). I'm not actually positive you need the PPA, I just have it because Chromium gets updated quite frequently. 
```
sudo apt-get install chromium-browser
``` To install it.

---

### Post by v1ad on 2010-07-23
apt-cache search is the best way 2 search for programs before you install.

(personally i install most of my programs through console. the gui is a lot slower (imo))

---

### Post by oldos2er on 2010-07-23
You can use Tab completion with package names (as well as commands). ```
sudo apt-get install chromi[Tab]
``` will show all packages beginning with the letters "chromi"

---

### Post by marshmallow1304 on 2010-07-23
```
chromium-browser --version
```

---

### Post by COKEDUDE on 2010-07-30
> **oldos2er said:**
> You can use Tab completion with package names (as well as commands). ```
sudo apt-get install chromi[Tab]
``` will show all packages beginning with the letters "chromi"

I really like that tab trick :). Thank you for that. 

> **marshmallow1304 said:**
> ```
chromium-browser --version
```

Oops. Thank you for pointing that out.

---

