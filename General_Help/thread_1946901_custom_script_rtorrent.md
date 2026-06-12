---
title: "custom script rtorrent"
date: 2012-03-25
forum: General Help
---

### Post by matt_symes on 2012-03-25
Hi

Does anybody know if it's possible to run a custom script from rtorrent after it has finished downloading an item.

I am currently downloading podcasts and moving them to a new directory after they have finished downloading; all from rtorrent. 

However, i also want to call a script that will transcode them after these steps. Is it possible to do this and to pass the name of the moved file to the script ? 

Writing the script is  not the problem and I realise i can write an independent script, using inotify-tools or some-such, to do this but i would prefer write a script i can call directly from rtorrent.

I can't seem to find info on how to this this on the net. My google-fu skill are letting me down :) 

How do you call a custom script from rtorrent after it has moved files ?

Any ideas anybody ?

Kind regards

---

### Post by TeoBigusGeekus on 2012-03-26
Add this
```
system.method.set_key=event.download.finished,put_a_name_for_the_action_here,"execute=/path/scriptname,$d.get_base_path="
```
to your .rtorrent.rc file and have your script manipulate the input file as normal user input ie. $1.

---

### Post by matt_symes on 2012-03-26
Hi Teo

> **TeoBigusGeekus said:**
> Add this
```
system.method.set_key=event.download.finished,put_a_name_for_the_action_here,"execute=/path/scriptname,$d.get_base_path="
```
to your .rtorrent.rc file and have your script manipulate the input file as normal user input ie. $1.

I didn't realise it would be as simple as that. Thanks Teo.

I think my major concern was getting the name of the file into the script that had just been moved.

Cheers mate.

EDIT: 

Just ran a quick test with a simple script. Worked perfectly ! Now on to write the main script.

Once again, thankyou Teo.

---

### Post by TeoBigusGeekus on 2012-03-27
You're welcome mate.

---

