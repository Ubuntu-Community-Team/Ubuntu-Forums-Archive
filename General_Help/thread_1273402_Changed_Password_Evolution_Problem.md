---
title: "Changed Password Evolution Problem"
date: 2009-09-23
forum: General Help
---

### Post by PostChache on 2009-09-23
I've recently changed the password for my account and now every time I open Evolution it asks me for my old password. How can I make it use my new password instead of my old one?

---

### Post by community nerd on 2009-09-23
What do you mean it asks you for your old password? What happens if you type your new password?

---

### Post by PostChache on 2009-09-23
> **community nerd said:**
> What do you mean it asks you for your old password? What happens if you type your new password?
It tells me the application 'evolution' (/usr/bin/evolution) wants to agree to my keys (key ring) but it's blocked.

Sorry that's a translation xD if I try to put in my new password it just keeps asking me the same thing and after I put in my password it will go straight to my email but if I push cancel I have to do it multipul times then it asks me for my email password. I'm guessing I have to change something with my keys to my new password as well?

---

### Post by community nerd on 2009-09-23
Or try re-entering it under EDIT>PREFERENCES

---

### Post by PostChache on 2009-09-23
> **community nerd said:**
> Or try re-entering it under EDIT>PREFERENCES
Where would I do that under Preferences? I've gone through it a couple of times but I can't find one that deals with a password other than my Email password

---

### Post by howefield on 2009-09-23
You could try the "Forget Passwords" option in the file menu.

Close and reload Evolution, enter new password and hopefully.....

---

### Post by community nerd on 2009-09-23
If you have changed your password since you first installed ubuntu then your keyring password is not the same as your ubuntu login password. A keyring keeps all your passwords so you dont have to type it every single time.  If you dont know your original password, go to Applications>Accessories>Passwords and Encryption keys. Click on Edit>Preferences> Highlight the current key and click Remove Key. Then add a key and remember that password! next time you type your evolution password and it asks you for the keyring password, enter it! Good luck.

---

### Post by PostChache on 2009-09-23
> **howefield said:**
> You could try the "Forget Passwords" option in the file menu.

Close and reload Evolution, enter new password and hopefully.....

Okay that worked, thank you very much!

Thank you as well community nerd.

---

### Post by howefield on 2009-09-23
> **PostChache said:**
> Okay that worked, thank you very much!

No problem, glad you're sorted.

---

