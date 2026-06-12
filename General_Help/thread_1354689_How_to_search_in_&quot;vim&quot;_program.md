---
title: "How to search in &quot;vim&quot; program?"
date: 2009-12-14
forum: General Help
---

### Post by abcuser on 2009-12-14
Hi,
I know to start search I can enter <Esc>, then / character and enter search string.

For example I write: "/Ubuntu Servere" (without double quotes) and there is no result string that would match the search string, because there is typo in search string, so I need to retype all the string "/Ubuntu Server". Is there any way I could edit search string and just edit search string and repair the error?
Regards

---

### Post by squaregoldfish on 2009-12-14
After you type the slash to search, simply use the up and down keys to find previous search strings - then you can edit them.

Steve.

---

### Post by abcuser on 2009-12-14
squaregoldfish,
no, you don't understand what I would like to do. Let me write simple sample:
1. In vim I try to search string, so I write:
/Ubuntu Servere
the above is a typo it should be Server instead of Servere, but this time I don't notices the typo.
2. I hit <enter> and get error: "Patern not found: Ubuntu Servere
3. When I press / character I lose all text typed in in step one, so I have to type one more time:
/Ubuntu Server
I would just like to edit string "/Ubuntu Servere" to "/Ubuntu Server". I hate to write all the search string one more time.

How to edit "/search string" in such a way I would not need to write all the string again? I would just like to delete "e" character from the search string.
Regards

---

### Post by squaregoldfish on 2009-12-14
Hmm. I still think what I suggested will work. Try this sequence:

1. In vim I try to search string, so I write:
/Ubuntu Servere
the above is a typo it should be Server instead of Servere, but this time I don't notices the typo.
2. I hit <enter> and get error: "Patern not found: Ubuntu Servere
3. Press /
4. Press the up arrow
5. You should see your previous search (Ubuntu Servere) which you can then change at will - in your case, just delete the last character, but you can use the arrow keys to move around and change any part of the string you like.

If this isn't what you're asking for, I'm afraid I'm totally lost.

Steve.

---

### Post by abcuser on 2009-12-14
squaregoldfish,
I am very sorry. Your first post was already the answer I was looking for. I just misunderstood it. Thanks a lot for help. Problem solved.
Regards

---

### Post by squaregoldfish on 2009-12-14
No problem. Misunderstanding people is spectacularly easy to do!

---

