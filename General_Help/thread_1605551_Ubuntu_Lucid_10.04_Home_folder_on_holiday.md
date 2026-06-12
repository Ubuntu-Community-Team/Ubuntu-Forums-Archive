---
title: "Ubuntu Lucid 10.04 Home folder on holiday"
date: 2010-10-25
forum: General Help
---

### Post by M-athia-s on 2010-10-25
Hi,

I'm on a 64-bit lucid 10.04 desktop version(acer laptop).
Today when I came back home from work and turned the pc on I heard the annoying startup sound from my speakers, indicating that something was wrong cause as I remember it, one of the first things I usually do is to turn off the boot sound on a fresh install.

Logged in just to be meet by next surprise, my home folder is gone and replaced by one that looks like it used to be on a fresh install... all the files etc is gone.

One of last things I did yesterday was to remove all the keys I had imported in gpg by first exportign them with gpg --list-keys > keys and then iterated over the keys with a small bash script: for key in $(cat keys) do gpg --delete-key $key
done

As i recall it, I also removed some files in the .Private folder.

It worked and I had no problem with that sequence. However can this be the issue that lead to my home folder disappearing? Sound strange to me.

I had a lot of project code that I had saved in my home folder that now seems gone. I can see that things I have placed elsewhere is still there so this is absolutely an issue only related to my home folder. And I know I should have made a backup but I just installed the dist.. and hadn't found the time to it. 
   
Is there any (free)undelete software out there that someone could recommend? Or anything else for the matter that can bring my old home folder back would be greatly appreciated. The files must still be on the disk cause I haven't written anything new to it.

BR,
Mathias

---

