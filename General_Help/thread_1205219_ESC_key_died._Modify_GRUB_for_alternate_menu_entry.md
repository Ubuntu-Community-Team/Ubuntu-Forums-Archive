---
title: "ESC key died. Modify GRUB for alternate menu entry?"
date: 2009-07-05
forum: General Help
---

### Post by chuzie on 2009-07-05
So I had the 1qaz, shift, caps, ESC, and tab keys die on my other laptop and now cannot access my GRUB menu due to lack of ESC key. Is there a way to modify the grub to use a different key besides ESC?
 
Thx.

---

### Post by taurus on 2009-07-05
Why not just comment out the hiddenmenu option in /boot/grub/menu.lst so you don't have to press any key to bring it up?

```
**[COLOR="Blue"]#[/COLOR]**hiddenmenu
```

---

### Post by John Private on 2009-07-05
> **taurus said:**
> Why not just comment out the hiddenmenu option in /boot/grub/menu.lst so you don't have to press any key to bring it up?

```
**[COLOR=Blue]#[/COLOR]**hiddenmenu
```Sorry for saying this so off topic but WOW 30k Posts 0.0.

---

### Post by chuzie on 2009-07-05
Thanks. I am a dummy for not thinking of that in the first place.

---

### Post by chuzie on 2009-07-05
The whole dead keys thing brinkgs up another issue that I will post elsewhere I my search comes up empty. Now that I am back in Ubuntu, I can't unlock my keyring b/c my password included some of the dead keys. Guess I need to search for a keymapper or the source of the keyring password.

---

### Post by Jebtrix on 2009-07-05
You could do some key mapping magic with xmodmap but the simpler thing to do is just run Applications > Accessories > Character Map (charmap). Then you can dbl click the letters/numbers/symbols you need to construct the word and copy+paste that to the password message box.

---

### Post by t4thfavor on 2009-07-05
Am I the only one who has 50 USB keyboards laying around?

depending on the model, you should be able to find a kb for your lappy for around 20USD.

---

