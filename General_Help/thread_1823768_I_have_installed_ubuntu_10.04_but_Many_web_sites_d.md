---
title: "I have installed ubuntu 10.04 but Many web sites dont repond me"
date: 2011-08-12
forum: General Help
---

### Post by Nasrine on 2011-08-12
Hi , 

Hope that someone could help, am struggling a lot for many days , actually my problem is I cannot access on some  web site like monster.com or facebook.com or hotmail.com and others , however the connection is ok i can get easily on my gmail.com or wikepedia or euronews , the web sites I have mentioned above they do not repond me after trying to log in or clicking on a link and am endless wating.

Am on Ubutu 10.04 LTS - the Lucid Lynx - released in April 2010 .
 I use Wifii connection i have added the two dns server name 8.8.8.8 and 8.8.4.4, I have checked my host file if there is not any 0.0.0.0 and i wanted to make to check my iptables but actually could not open it ...

I have tried with Firefox, chrome and opera, all have the same behavior , 

I did not able the firewall that comes by default , 


Any ideas please ?

Thank you

Nasrine

---

### Post by SavageWolf on 2011-08-12
Have you tried disabling your two DNS servers? (Selecting it to do it automatically.)

---

### Post by Nasrine on 2011-08-12
HI , you mean the 8.8.8.8 and 8.8.4.4 ? or the old one , ? i  added the two by using network connection and to answer you i have just opened the resolv.conf and i can read there is only those two ,

---

### Post by b0b138 on 2011-08-12
dont use 8.8.8.8 or 8.8.4.4.  Set it to automatic and see if that works

---

### Post by Nasrine on 2011-08-12
it was automatic before and it did not work so that's why i have tried the 8.8.8.8 and 8.8.4.4 , so i dont understand what is happening, Does it mean i can send package to those web site and they cannot answer me because they dont receive my package properly or because i cannot receive theirs answer? ? anyway in both cases and of course is something to do with my machine ,  is it something to do  with my IP ? ??  i precise that pinging facebook for example works fine,

---

### Post by mike555 on 2011-08-12
So , your saying you can go on those sites but when you click on something you can't go to the clicked on sites??

 maybe their looking for Internet Explorer , you might try the Firefox add-on "User Agent Switcher" to let them sites think your using IE...

 or perhaps you need a codec, did you install Ubuntu extras?

---

### Post by Nasrine on 2011-08-12
But why should I let them think  that am using internet explorer ? Firefox another are able to connect to any web site without letting them think that they are not ......anyway i add it to check and still dont work at least  if I need to restart my laptop !!!!...........PLEASE HELP , I really dont find the solution ,

---

### Post by SavageWolf on 2011-08-12
Facebook and that lot don't look for IE or need codecs...

What happens if you go here? [http://www.savagewolf.org/yay.html](http://www.savagewolf.org/yay.html)

What do you mean "endless waiting"? Does the pageitself  display a "waiting..." or "loading..." thing.

What direction is the load indicator in the tab spinning (Chrome) or what colour is it (Firefox)?

When you try to log in or whatever, make sure the system monitor is open, and tell us if "Network History" (Under "Resources") is a decent amount. (Not zero)

---

### Post by Nasrine on 2011-08-12
I clicked on [http://www.savagewolf.org/yay.html](http://www.savagewolf.org/yay.html) and i got a pop up saying ''yah ''.

Yes on chrome I can have the page then is says upload and shows 0%upload in the bottom and then nothing comes like still loading, on firefox is red and still loading and nothing comes too, the red thing is like stuck.

IN the system monitor i have the line for sending the purple one is almost at zero with some variation and the the blue one for receiving is upper but almost zero with big variation to up , it says in the total receiving 15.1 MiB ( am still loading facebook on the two browser) and in the sending 2.6 Mib,  then the page on Chrome become all white and the loader has stopped.

---

### Post by Nasrine on 2011-08-12
The connection was reset

      
       
I got this message on Firefox:    
        
        


The connection to the server was reset while the page was loading.         
      

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to ac

---

### Post by Habitual on 2011-08-12
have a router?

---

### Post by Nasrine on 2011-08-13
NO i dont have , i use a wireless connection that I dont manage, I was using this same connection with my previous windows vista and all was fine,

---

### Post by mastablasta on 2011-08-13
well wireless connection has to go through router/or wireless moedm and someone manages it. it could be they blocked access to those sites.

---

### Post by Nasrine on 2011-08-13
I dont think so because my flatemate has windows ans she can access on any web site,

---

### Post by Nasrine on 2011-08-13
Does someone know how can I check my MTU value ? I have done this and i think that 1500 is the  recommended one but what the line below mean ?


nesrine@nasrid:~$ sudo tracepath myDefaultRoute
 1:  nasrid.local (myIP)                                                     0.154ms pmtu 1500
 1:  myDefautlRoute (myDefaultRoute)                              3.049ms reached
 1:   myDefautlRoute (myDefaultRoute)                              4.149ms reached
     Resume: pmtu 1500 hops 1 back 64

---

### Post by Nasrine on 2011-08-30
Finally I found the solution thanks to this article [http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon#comment-75263](http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon#comment-75263)
The solution is to start firestarter and select IP are assigned via DHCP .

---

