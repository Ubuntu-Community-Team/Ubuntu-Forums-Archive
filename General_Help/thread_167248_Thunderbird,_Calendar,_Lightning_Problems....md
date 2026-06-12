---
title: "Thunderbird, Calendar, Lightning Problems..."
date: 2006-04-28
forum: General Help
---

### Post by mlissner on 2006-04-28
So, until today I had thunderbird working marvelously. Then, it occured to me that I wanted it to remind me about something in a week, and that there might be a calendar extension.

Lo and Behold, there was. I went to install it (Calendar). It wouldn't install because I had the Ubuntu version of Thunderbird (1.0.*), not the Thunderbird version (1.5.*). So, what did I do? I installed 1.5. No issues there, except that it wasn't an intuitive install, but whatever. 

Next, I went to install the Calendar Extension. Success!! It worked, but it wasn't very integrated into Thunderbird. Then I saw another extension, Lighning that promised to be better than Calendar - more integrated no less. Installed! Success!

Then things started getting bad...After installing both of those extensions, I had some minor issues with Lightning reframing my screen so there was a huge gray area at the bottom at all times..."no big deal" I thought. It's probably because I have two calendar extensions, and they must be fighting for the rights to my computer (or something). I'll uninstall them both, close thunderbird, reopen Thunderbird, and then reinstall the better of the two.

I went to the Extension manager, uninstalled both, and closed Thunderbird. Then I went to reopen Thunderbird. Nothing. I tried the terminal:
```
mozilla-thunderbird.ubuntu
selected locale:en-US

run-mozilla.sh: Cannot execute /usr/lib/mozilla-thunderbird/mozilla-thunderbird.ubuntu-bin.
```

Still nothing...interesting...maybe I used ```
mozilla-thunderbird
```, rather than ```
mozilla-thunderbird.ubuntu
```. I'll try that.

That one does NOTHING, but I did determine that it was the command that worked in the past by checking what my shortcuts did when clicked. So...can somebody tell me how to make this work...perferrably fast? I'm going on a business trip tomorrow, and I'd love to have this fixed before then...any ideas that might make Thunderbird actually open...if there was even a verbose way of starting Thunderbird, that might help, but I couldn't figure out how to do that either...

---

### Post by EndersGame on 2006-04-28
Lightning tends to be very picky about the compiler that was used to build Thunderbird.  There have been some reports that the Ubuntu supplied version of Thunderbird causes problems because of this.  Try downloading the official thunderbird package from mozilla.com and installing Lightning in that.  It should work better.  To get Thunderbird to simply open, try running it in safe mode ([http://kb.mozillazine.org/Safe_mode](http://kb.mozillazine.org/Safe_mode))

---

### Post by reubadoob on 2006-05-01
Thought I'd post my Thunderbird problem here before making a new thread.

Before using Ubunut I used Thunderbird to retrieve my GMail. However now that I'm using Ubuntu & Thunderbird 1.5 I keep recieving a timeout error when trying to download my GMail emails. Thunderbird 1.5 does do an excellent job of retrieveing my Roadrunner & Univeristy email just fine. The only problem arises when trying to get my GMail.

---

