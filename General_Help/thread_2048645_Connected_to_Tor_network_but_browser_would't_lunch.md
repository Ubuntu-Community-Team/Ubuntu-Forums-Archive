---
title: "Connected to Tor network but browser would't lunch"
date: 2012-08-27
forum: General Help
---

### Post by xgtyca on 2012-08-27
I am beginner user to Ubuntu, when i was using 11.04 and 11.10 I used Tor perfectly. But since I started using 12.04, I had had several problems. One of main problems for me is when I download the latest tor browser bundle from tor website, it does not work properly. The program lunch and takes time to connect to tor network, after connecting Firefox should lunch automatically, but it does not. Can Anybody help me please?

Thanks in advance:popcorn:

---

### Post by zeroseven0183 on 2012-08-27
I wonder if you have a Firefox window opened already? If yes, you might want to try closing it first before launching Tor.

---

### Post by xgtyca on 2012-08-27
The same idea came to me and I tried it but it did not work also
I closed Firefox and lunch tor but the browser did not lunch  ):P

---

### Post by jim_deadlock on 2012-08-27
Are you sure Vidalia is fully connected and you have a green onion icon? You must have a green onion before the browser's lunchtime.

---

### Post by xgtyca on 2012-08-27
Yes the onion is green

---

### Post by jim_deadlock on 2012-08-27
Open your System Monitor and go to the processes tab. When you start the bundle you should see the following processes appear on the list:

**start-tor-browser** (this is what you should initially run)
**tor** (starts automatically)
**vidalia** (starts automatically)
**firefox** (normally appears once tor has connected, as we discussed)

If you have any of those already running before you start then you should end them before starting.

---

### Post by Statia on 2012-08-27
> **xgtyca said:**
> The same idea came to me and I tried it but it did not work also
I closed Firefox and lunch tor but the browser did not lunch  ):P

Maybe it wasn't hungry? Try later in the day ;)

---

### Post by xgtyca on 2012-08-27
> **jim_deadlock said:**
> Open your System Monitor and go to the processes tab. When you start the bundle you should see the following processes appear on the list:

**start-tor-browser** (this is what you should initially run)
**tor** (starts automatically)
**vidalia** (starts automatically)
**firefox** (normally appears once tor has connected, as we discussed)

If you have any of those already running before you start then you should end them before starting.


I did as you said and none of them was open before running tor and after  I run tor all of them appear in the list except firefox

---

### Post by ottosykora on 2012-08-27
in some versions the browser is called aurora.
check for  that.

Otherwise simply get other copy of the bundle, and try again.

---

### Post by xgtyca on 2012-08-28
> **ottosykora said:**
> in some versions the browser is called aurora.
check for  that.

Otherwise simply get other copy of the bundle, and try again.

I know that it might be named Aurora, But again nothing starts after connecting to TOR network
[SIZE=3]I have the green onion, its saying you are connected to tor network but nothing after that. Can any body help me with this problrm?
I am tired of this problem as since I started using 12.04 in April and every time i need to use tor i have to go windows. Its very strange, Ubuntu should be better than windows in every thing. Tor was working perfectly in 11.04 and 11.10, What happened???!!![/SIZE]](*,):-k

---

### Post by xgtyca on 2012-08-28
[SIZE=4][COLOR=Red]Cannot any body help me with this problem???!!![/COLOR][/SIZE]   ](*,):-k
[SIZE=4][COLOR=Red]Where and who I should ask?[/COLOR][/SIZE]

---

### Post by lpm on 2013-02-20
Morning all,
 I am having the same problem, I’m running 12.10 on an older system and it works brilliant, so fast compared to windows, but to use tor i have to use a windows system, i don’t wont to touch windows so please someone help?):P

---

### Post by rami on 2013-06-22
I had the same problem after deciding to place tor-bundle in /opt. sudo mv it automatically changed the ownership to root. So you either do a 

> sudo chown username tor-bundle

Or just extract the bundle in ~/.tor-bundle

Point in case, make sure you own it not root. And do NOT run it as root!

---

