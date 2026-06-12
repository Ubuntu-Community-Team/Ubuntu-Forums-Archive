---
title: "notify-send to remote computer help"
date: 2009-07-25
forum: General Help
---

### Post by Space-Age on 2009-07-25
For the last couple days, I've been playing around with pygnotify, and have been able to get my Ubuntu machine to send Growls, both locally and accross the internet, to my Macs.  Now, I'm trying to do a similar thing, but between two Ubuntu hosts in the LAN, and am having a difficult time.

I can use notify-send *subject* *text* to growl locally, but how would I go about doing this to another host.  ie. I'd like one Ubuntu server to tell the other Ubuntu machine on the LAN that it will be shutting down soon. etc.

Any thoughts on how I'd go about doing this?

---

### Post by Space-Age on 2009-07-29
A few more days tinkering around and reading-up, I've found a solution that works well (for me) for this.  I've written a python script (2 actually) to listen on the remote computer, then another to send from the client.  The client script takes parameters that define the message, and he server script listens on a fixed port, and passes the parameters on with notify-send.

---

### Post by drhabber on 2011-02-25
> **Space-Age said:**
> A few more days tinkering around and reading-up, I've found a solution that works well (for me) for this.  I've written a python script (2 actually) to listen on the remote computer, then another to send from the client.  The client script takes parameters that define the message, and he server script listens on a fixed port, and passes the parameters on with notify-send.

I'm looking for something like this for quite long now. Can you share your solution?

---

### Post by Space-Age on 2011-02-25
The two scripts I have echoserver and echoclient do (as respectively stated, listen and send on a specific port.

echosever.py
```

#!/usr/bin/env python 

# Network Listener for notify-send 

import socket 
import os

host = '' 
port = 50000 
backlog = 5 
size = 1024 
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM) 
s.bind((host,port)) 
s.listen(backlog) 
while 1: 
    client, address = s.accept() 
    data = client.recv(size) 
    if data: 
        client.send(data)
        cmd = 'notify-send ' + data
        os.system(cmd) 
    client.close()

```

echoclient.py
```

#!/usr/bin/env python 

#network notify-send 

import socket 
import sys

host = '192.168.1.10'  #server IP
port = 50000 
size = 1024
title = sys.argv[1]
message = sys.argv[2]
 
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM) 
s.connect((host,port)) 
s.send('\"' + title + '\" \"' +message+'"') 
data = s.recv(size) 
s.close() 

```

You need to start the server on one machine, then send the notify message using

./echoclient.py "title_goes_here" "message_goes_here"

let me know if that works for you.

---

### Post by drhabber on 2011-02-25
> **Space-Age said:**
> The two scripts I have echoserver and echoclient do (as respectively stated, listen and send on a specific port.

[...]

You need to start the server on one machine, then send the notify message using

./echoclient.py "title_goes_here" "message_goes_here"

let me know if that works for you.

It works flawlessly. You are my hero of the day :).

Now I'm able to display notifications from Finch IM that is running remotely. I've set the script as a custom sound command being run when a new message arrives. 

Thank you so much!

---

### Post by nicoceledon on 2011-11-22
Simple and usefull. Thanks

---

### Post by reagsuere on 2012-03-01
Few individuals just like having freckles therefore today I would like to advise on several ways to get rid of your freckles. These are merely suggestions, you could need to research additional into these to maximize their results.   [mielno](http://sarbinowo.nom.pl )   You are able to that by making a mix of preparing soft drinks and drinking water after which employing it to your face to get a very good 10 minutes, can lighten freckles. It's not an issue that works well with every person even so and may relax in your case. It is suggested to get this done at the very least five times before choosing whether or not it technique is for you.   [sarbinowo](http://sarbinowo.nom.pl )   The up grade to this is to find bleaching items that should help alter the hue of the freckles completely leaving you with the same coloration skin color. Needless to say you should seek advice from a doctor initial before you apply any lightening merchandise (no matter what it states on the package).   [chlopy](http://mielno-noclegi.mil.pl )   Lemon juice can get rid of freckles and whilst that might sound crazy, there were several positive results with this by many people. People do tend to be give up fair skinned however and it appears that it may just work for that one type of skin.   [chlopy](http://sarbinowo.mail.pl )   Freckles are usually a result of the sun, so if your out under the sun ensure that you use a hat! This can be vital as this could also present you with cancer which is a whole lot a whole lot worse then the couple of freckles.   [sarbinowo](http://sarbinowo.sex.pl )   Ascorbic Acid is additionally designed to help to crystal clear them up a bit. You may get this by making sure that you eat a lot of berries regularly. Your designed to take in 5 pieces daily at any rate and vit c is really healthy for you that you should do it even if you don't have freckles.   [mielno](http://mielno.mail.pl )   Last but not least, you can always disguise your freckles by putting on cosmetics. Even though this is not a supply of eliminate freckles, it lets you do support cover them up and make them less noticeable.   [chlopy](http://chlopy.travel.pl )

---

