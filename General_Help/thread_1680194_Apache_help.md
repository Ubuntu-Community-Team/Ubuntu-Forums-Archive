---
title: "Apache help"
date: 2011-02-02
forum: General Help
---

### Post by Nerflander on 2011-02-02
Hi there all ! I need some apache help. I have a second website on my webserver but now when i want to go to the addres of the website 

192.168.xx.xx/xxx it directs me to the one website that is already working.

Now my thoughts were ow hey that is a webadmin thing you know , redirect.

But i cant help to figur out what is cofigured wrong. I mean both websites are pointed to their own directory why would it be that it directs me to the other 1 ?:mad:

Hope someone knows something

---

### Post by indytim on 2011-02-02
I presume that you have both sites segregated by their own directory structure within /var/www.  I that is the case, then you would access each site as

```

http://localhost/site1/index.php
http://localhost/site2/index.php


```

Of course substitute the "site1" and "site2" for your installation.

Hope this helps.

IndyTim / DataMan

---

### Post by Nerflander on 2011-02-02
thats exactly what i am doing

for example we have

localhost/website1/index.php

but! 

when i go to 

localhost/website2/index.php

it actaully redirects me to the website1/index.php somehow?

---

### Post by indytim on 2011-02-02
post the contents of your 2 index pages.

-IndyTim / DataMan

---

### Post by Nerflander on 2011-02-02
I think this will do you more good. 
I cant give you all the contents i am afraid. but i think this is causing the problem. 

(just so you know i am not the programmer of this i am the system engineer and i already had contact with the developer and he hadt had a clue why he was doing that.)

* edited the source out * 

Il send it to your inbox.

---

### Post by indytim on 2011-02-02
To aid in your problem solving, suggest you throw a line of code in before your switch statement to see what $_SERVER['HTTP_HOST']  is coming in at as in:

> 
echo '<br>_SERVER[HTTP_HOST]='.$_SERVER['HTTP_POST'];


Once you know the value of the variable, you can look at your switch statement specifics.

IndyTim / DataMan

---

### Post by Nerflander on 2011-02-02
Alright what happend when i added the line of code :

The second website appeared! but!!

it appeared under the "website1" its domain name.

---

### Post by Nerflander on 2011-02-02
bump

---

