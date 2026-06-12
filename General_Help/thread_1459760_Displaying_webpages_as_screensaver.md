---
title: "Displaying webpages as screensaver"
date: 2010-04-21
forum: General Help
---

### Post by Tech_Spanky on 2010-04-21
Ok I have been working on a web based project and would like to make a kiosk type station for my users. This is easily accomplished with ubuntu and firefox and some add-ons (r-kiosk).  But what I want is when the terminal is idle, which it will be often, to cycle a short list of webpages from my app as a screensaver.  There is a screensaver for this in windows but who wants that.  I have spent several days googling this and have found this web site [http://mcmlxxii.co.uk/2009/04/19/turning-firefox-into-a-web-screensaver-using-a-bash-script/](http://mcmlxxii.co.uk/2009/04/19/turning-firefox-into-a-web-screensaver-using-a-bash-script/) and made the following script based on it(just a few changes so each page can be displayed for different times)
```

#!/bin/bash

remoteclient=$(find /usr/lib/ -type f -name mozilla-xremote-client | grep -m 1 xulrunner)

if [ `ps -e | grep firefox | wc -l` -eq 0 ]; then
	/usr/bin/firefox -fullscreen &
	sleep 5
fi

while [ `ps -e | grep firefox | wc -l` -gt 0 ]; do	
        while read url delay
	    do
	    $remoteclient -a firefox "openurl($url)"
            if [ $? -gt 0 ]; then
		echo "Firefox not running or ignoring me, bailing out......"
		killall firefox
		exit 0
	    fi
	    sleep $delay
	    done </home/dave/.pages
done
exit 0

```
I have read alot about xscreensaver and can get it to launch the script, but it still displays the screensaver and not fire fox.
Just wondering if anyone has done anything like this or anything to do with launching/killing a script when the computer is idle?

Thanks for any help

---

### Post by Tech_Spanky on 2010-04-23
No ever wanted webpages as a screensaver?

---

### Post by Tech_Spanky on 2010-04-30
bump

---

