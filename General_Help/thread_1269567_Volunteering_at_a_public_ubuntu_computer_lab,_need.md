---
title: "Volunteering at a public ubuntu computer lab, need help"
date: 2009-09-18
forum: General Help
---

### Post by Catalyst_Tech on 2009-09-18
I have some questions, as a intermediate level linux user

Is there a program I can use to allow users to create their own accounts w/o admin help?

Is there a way to sync a user's account and home folder to the other workstations when they log in?

Is there a way to remotely install updates or software on the workstations?

I'm also interested in any sites or blogs focusing on running a small public lab

Thank you in advance :-)

More info about the lab:

*Catalyst Community*

*Our Slogan: *[I]“Connect and Affect”

We accomplish the vision by catalyzing collaborative communities to build relationships, establish partnerships, inspire growth, and encourage contribution. [/I]

---

### Post by stderr on 2009-09-18
I'm afraid I don't have experience in establishing labs with these kind of requirements either. 

However, with regard to the first question, the easiest solution I can think of would be to create a new user account, limiting its permissions with the sudoers file (to adduser, and whatever else you need to make it work) & also setting NOPASSWD. You could then use that limited account for creating new users. It would only take a quick and easy BASH script which loops back to something like "To create a new account, please enter your first name:", before asking a list of questions, whilst you build enough information to run "sudo adduser ..." and create the account. You could just leave the machine running the script.

Another solution would be to do the same sort of thing, but set up a web interface for it. Then provide a limited user account to run firefox, lock it down to showing the one website... you could gnock up a GTK application... lots of possibilities.

I'm assuming, however, that you intend to run a machine as the "create a new account" machine,

---

