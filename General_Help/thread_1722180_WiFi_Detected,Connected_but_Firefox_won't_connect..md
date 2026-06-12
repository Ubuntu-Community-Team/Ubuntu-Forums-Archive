---
title: "WiFi Detected,Connected but Firefox won't connect."
date: 2011-04-05
forum: General Help
---

### Post by aggouras on 2011-04-05
Hello to the Ubuntu community! I joined a few minutes and as far as I am here, I think this forum is awesome. I am also a **complete beginner** to Ubuntu so please chill out.

Now to the point.

I've  installed Ubuntu 10.10 and everything went OK. It also found Wireless Networks. I am connecting to the same I do on Windows 7(yes dual boot).It asks for WEP, I put it and says Connection Established. But, when I open up Firefox to navigate to Google, it waits for 20 seconds and after that it pops an error that it couldn't establish a connection.

I would really appreciate if someone gave me a solution to this because I want to use Ubuntu for hacking..

Thanks. ):P

---

### Post by adit on 2011-04-05
Open the terminal and type
```
ping google.com
```
What output do you get?

---

### Post by aggouras on 2011-04-05
> **adit said:**
> Open the terminal and type
```
ping google.com
```What output do you get?
Thanks for fast reply.

The results are normal it says I get reply from google.com

```
bytes=32 Time=64ms TTL=52
```

---

### Post by adit on 2011-04-05
What is the output of
```
wget google.com
```
Please post the full output (not only the results).

---

### Post by NFblaze on 2011-04-05
What does the Firefox webpage say when you try to go to [www.google.com?](www.google.com?)

I have a hankering that the default Tor proxy might be enabled or the Network settings in Firefox are enabled.

---

### Post by aggouras on 2011-04-06
> **NFblaze said:**
> What does the Firefox webpage say when you try to go to [www.google.com?]("http://www.google.com?")

I have a hankering that the default Tor proxy might be enabled or the Network settings in Firefox are enabled.


I've disabled the Firefox proxy but no luck. 
The connection has timed out

      

      
      
      

      
        
        

          

The server at [www.google.com](www.google.com) is taking too long to respond.

        


        
        


    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web

---

### Post by aggouras on 2011-04-06
> **adit said:**
> What is the output of
```
wget google.com
```Please post the full output (not only the results).

.













--2011-04-06 14:45:57--  [http://google.com/](http://google.com/)
Resolving google.com... 209.85.147.104, 209.85.147.105, 209.85.147.106, ...
Connecting to google.com|209.85.147.104|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.google.com/](http://www.google.com/) [following]
--2011-04-06 14:45:59--  [http://www.google.com/](http://www.google.com/)
Resolving [www.google.com](www.google.com)... 209.85.147.106, 209.85.147.147, 209.85.147.99, ...
Reusing existing connection to google.com:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.google.gr/](http://www.google.gr/) [following]
--2011-04-06 14:45:59--  [http://www.google.gr/](http://www.google.gr/)
Resolving [www.google.gr](www.google.gr)... 209.85.147.104, 209.85.147.105, 209.85.147.106, ...
Reusing existing connection to google.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [        <=>                            ] 9,557       7.37K/s   in 6.3s    

2011-04-06 14:46:08 (1.47 KB/s) - `index.html' saved [9

---

### Post by adit on 2011-04-06
The output of wget shows that there is no problem with your network.  The problem is with firefox settings.
In the firefox connection settings dialog box there are 5 radio buttons.  Try one by one.  One of these 5 things will work.

---

### Post by aggouras on 2011-04-08
Unfortunatelly, I had already tried all of 5 radio buttons but none of them worked.

I forgot to mention that even when I type a  "sudo apt-get" command, I get an error that It couldn't locate the package xxxx.

Example : 

```
sudo apt-get install aircrack-ng
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aircrack-ng
``` 
What should I do?

---

### Post by adit on 2011-04-08
I don't know the solution to your firefox problem. Only thing I can say is your network is  normal because the program wget downloaded the file successfully. My suggestions:
1) Try other browsers like opera, chromium
2) If you just want to download a file use this command:
wget url_of_the_file
For your another problem I want to read your file:
/etc/apt/sources.list
Copy and paste that file

---

### Post by tillerdemon on 2011-04-08
What Router are you using? I have had that same problem with 10.10 with the  802.11b frequency, however worked fine with 10.04.

---

### Post by 3rdalbum on 2011-04-08
> **aggouras said:**
> ...It asks for WEP, I put it and says Connection Established....
I would really appreciate if someone gave me a solution to this because I want to use Ubuntu for hacking..

This is a little bit off-topic, but it looks like the hacker could become the hacked. WEP is notoriously insecure, only barely better than no encryption. Use WPA2 instead. You don't need Aircrack to tell you that your WEP network is an open target.

Try a different web browser (e.g. Chromium) and see if your immediate problem still occurs?

---

### Post by aggouras on 2011-04-08
> **tillerdemon said:**
> What Router are you using? I have had that same problem with 10.10 with the  802.11b frequency, however worked fine with 10.04.

I am on 802.11g

---

### Post by aggouras on 2011-04-08
> **3rdalbum said:**
> This is a little bit off-topic, but it looks like the hacker could become the hacked. WEP is notoriously insecure, only barely better than no encryption. Use WPA2 instead. You don't need Aircrack to tell you that your WEP network is an open target.

Try a different web browser (e.g. Chromium) and see if your immediate problem still occurs?
I know. Because it is not mine. I used aircrack in Backtrack 4 to hack it but I want to use Ubuntu. :)

---

### Post by aggouras on 2011-04-13
BUMP..I tried with Google Chrome but It didn't work. I am getting frustrated.

---

