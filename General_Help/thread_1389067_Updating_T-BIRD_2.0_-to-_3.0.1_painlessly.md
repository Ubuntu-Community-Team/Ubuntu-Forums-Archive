---
title: "Updating T-BIRD 2.0 -to- 3.0.1 painlessly?"
date: 2010-01-23
forum: General Help
---

### Post by sandman3838 on 2010-01-23
Hello

I have been using Thunderbird 2.0 for sometime and it's been great.
However I would like to update to 3.0. without loosing any of my current Email settings.  Do any of you have suggestions for a painless way to the update.

Also like with Firefox which updates automatically, is it possible to setup the some option for Thunderbird as well?

Now so far I have found this, but the way it was worded I not sure if this is for a New Install or an update?  Suggestions anyone?

To install follow the steps below:

1. Open Terminal

2. Add Mozilla's sources by:
    sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa

3. sudo aptitude update

4. sudo aptitude install thunderbird-3.0 thunderbird-3.0-gnome-support

5. sudo aptitude remove thunderbird-2.0 thunderbird-2.0-gnome-support

6. sudo ln -s /usr/bin/thunderbird-3.0 /usr/bin/thunderbird


Thank you everyone for all your help!

---

