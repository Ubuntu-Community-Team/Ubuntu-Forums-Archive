---
title: "Unable to logout !"
date: 2010-05-13
forum: General Help
---

### Post by Onesimus on 2010-05-13
I am using Ubuntu 10.04 and am unable to logout.

I click on logout, and nothing happens.  I get a prompt asking whether this is what I want to do, and then nothing !

Any help would be greatly appreciated.

---

### Post by Smart Viking on 2010-05-13
I just had the same problem. Open the terminal and type:

gnome-session-save --kill

If remember right. :)

EDIT: Oh, i didn't have  the same problem, my problem was that the logout button simply was not visible.

---

### Post by howefield on 2010-05-13
> **Onesimus said:**
> I get a prompt asking whether this is what I want to do, and then nothing !

And the prompt says what ?

Does it look like this...

---

### Post by Onesimus on 2010-05-13
> **howefield said:**
> And the prompt says what ?

Does it look like this...


Yes it does.

---

### Post by Smart Viking on 2010-05-13
> **Onesimus said:**
> Yes it does.

What does it say when you enter my command? It is worth a try, since that is the command to log out from the terminal.

---

### Post by Onesimus on 2010-05-13
> **Smart Viking said:**
> What does it say when you enter my command? It is worth a try, since that is the command to log out from the terminal.

I get a slightly different prompt, and then nothing.

I know I should be using Ubuntu all the time, but I just wanted to logout :)

---

### Post by Onesimus on 2010-05-13
@Smart Viking.

You put me on the right track.  I looked at the man pages of 

gnome-session-save

and there was an option to --force-logout.  It appears that openoffice Quickstarter was the culprit.

many thanks

---

