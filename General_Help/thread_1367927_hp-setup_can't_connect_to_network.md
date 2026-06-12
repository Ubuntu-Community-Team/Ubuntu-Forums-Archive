---
title: "hp-setup can't connect to network"
date: 2009-12-30
forum: General Help
---

### Post by texpat on 2009-12-30
Title sums it up:

I run [FONT="Courier New"]sudo hp-setup -i[/FONT], confirm whatever options I'm given (connection, device name and so on) until I get to the bit about downloading the plugin. It says it tries to connect to the network and gives up after 10 seconds or so, displaying an error message [FONT="Courier New"]error: network connection not detected.[/FONT]

I'm using hplip 3.9.8 on 64bit Karmic.
As far as I can judge my network connection is OK (www, email and ping so far work nicely).

I'd be really grateful for any ideas or solutions for this.

Thanx

tex

---

### Post by texpat on 2009-12-30
Bump.

Oh dear. Bit of a faux-pas, right? Sorry for that.

---

### Post by Mark Phelps on 2009-12-30
Stop bumping!! Rule of thumb around here is to bump once every 24 hours -- not every few hours.  Your impatience is not going to get you help any faster.

---

### Post by texpat on 2010-01-07
After much fiddling and trying things out, I finally came across [[COLOR="Blue"]this thread on Launchpad[/COLOR]]("https://answers.launchpad.net/hplip/+question/41899"), where one Aaron Albright suggests to try the following:
```
cd hplip-2.8.7
./install.py -n
```
Use the correct hplip version number, of course.
This runs the installation script that - among others - sorts out dependency issues downloading packages as needed (which is where my problems originally had started) and setting things up.

Two caveats, however:

[LIST=1]
[*]I have no idea why this script didn't produce network connection errors.
[*]Although it worked for me, the quality of colour prints on my Color LaserJet 2600n is really bad (b/w OK, though).
[/LIST]
Thus, this is a (partial) solution to the issue at hand. Hope others can use this should they run into similar problems.

---

### Post by ianstump on 2010-05-19
Hi, texpat, can you please post exact instructions on how to make it work...
I just cant make it happen...... :(

Thanks

---

### Post by robinparriath on 2010-07-27
Thanks!
 ./install.py -n worked for me.

Looks like it relaxes the wait time for the connection to be established, which was what I needed.

---

### Post by Biscuit 85 on 2010-09-18
It helped me too! I find Ubuntu really hard to get a grasp on, but on my quest to solve my HP printer installation dilemma, this was the solution, so THANK-YOU!!:guitar:

---

