---
title: "f-spot import permisions"
date: 2006-04-15
forum: General Help
---

### Post by junior aspirin on 2006-04-15
hi. i am having problems with f-spot on dapper (i posted here as it is a general linux problem)

i have 3 user accounts on my pc. i set up a folder /home/shared to store documents that anyone on the computer can have access to. i have the ownership of that folder set the permisions as rwx for the owner and a group that the 3 users are members of. in side the "shared" folder i have a subflder of "photos" which is where i would like my photographs imported to.
for this task i thought f-spot would be the best solution.

i have symlinked the config file of f-spot (~/.gnome2/f-spot) to a location in the shared folder. and have given it rw permisions for the owner and group. i have also symlinked the photos folder to each of the accounts home folder called "photos".

this is my problem: when i import the photographs from my digital camera through f-spot's import tool the permisions are only set as rw for the owner (ie the person who imported the photos).  another account member cannot see the photos since the permisions are set to be rw as the owner only. i need the permisions to be set to be read by the group.

i think that is clear. this is anoying since the people using the pc are not good with computers, so running chmod is not an option, or ideal. any ideas on how i can solve this?

---

### Post by junior aspirin on 2006-04-19
bump?

---

