---
title: "Lubuntu on the AA1 Storage Expansion"
date: 2011-08-23
forum: General Help
---

### Post by pjalegria on 2011-08-23
Does anyone now if its possible to "join" SD card at storage expansion with home partition like in linpus???

---

### Post by tredegar on 2011-08-23
Probably, but I know nothing about linpus (but I've read a lot of complaints about it).

As usual with linux, there are many different ways to achieve what you want.

If you need more space for your home you can:

1] Mount the SD card to a directory in your home like **/home/pjalegria/extrastorage**

2] Copy all of your **/home/pjalegria/*** to the SD card partition and then have that mounted as **/home/pjalegria/** when your machine boots. Your home will then be the size of the SD card partition.

3] There may be other suggestions.

4] Use Logical Volume Management (which I do not like, and have never used, so it's my last suggestion).

Read up, and choose......

---

### Post by pjalegria on 2011-08-23
Please, can you give detailed instructions to do that? thanks

---

### Post by tredegar on 2011-08-24
> Please, can you give detailed instructions to do that?
What is "that"?
I offered you three choices, the last of which I have no experience of.
As I said, read up, and choose.

---

### Post by pjalegria on 2011-08-24
Option 2, sorry

---

### Post by tredegar on 2011-08-24
OK. 

Option 2 it is then.

I have already posted a reasonably detailed HOWTO [here]("http://www.linuxquestions.org/questions/linux-desktop-74/move-home-to-partition-after-install-871764/#post4307855")

If you don't understand the instructions there, please, at least, make an effort to educate yourself about what the commands do and how they work.

If you continue to run into problems, come back here. We'll do our best to help you, but evidence of some effort from yourself, to help yourself learn, will be appreciated.

Best wishes.

---

