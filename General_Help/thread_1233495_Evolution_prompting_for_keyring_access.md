---
title: "Evolution prompting for keyring access"
date: 2009-08-06
forum: General Help
---

### Post by n.hinton on 2009-08-06
Slightly irritated by Evolution prompting for keyring access the first time its run after boot.

I made a new keyring and called it home then deleted the default,  re-entered all passwords and nothing changed Evolution still prompts.

I have two files in ~/.gnome2/keyrings: 
home.keyring and default

Default is a plain text file containing the word home

I have seen many posts suggesting 
&#8220;echo -n default > ~/.gnome2/keyrings/default&#8221; 
(which in my case would have to be
 &#8220;echo -n home > ~/.gnome2/keyrings/default&#8221;)
which seems to me a very long handed way of typing the word default into a text file.

The prompt says the keyring is locked, a quick check of &#8220;passwords and encryption keys&#8221; shows it isn't, so why can not Evolution retrieve the pop passwords it needs. Strongly suspect this is a bug or bugs.

If anyone has a solution or workaround, myself and I'm sure many others  would be very grateful.

---

### Post by malel on 2009-08-06
I am having the same problem and find it most irritating. Is there some way I can get rid of this 'Keyring' thingie altogether.

cheers

---

### Post by n.hinton on 2009-08-07
> **malel said:**
> I am having the same problem and find it most irritating. Is there some way I can get rid of this 'Keyring' thingie altogether.

cheers

Yes I'm sure were not alone!

---

