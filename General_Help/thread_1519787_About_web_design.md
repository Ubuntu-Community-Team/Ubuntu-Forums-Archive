---
title: "About web design"
date: 2010-06-28
forum: General Help
---

### Post by Zerocool Djx on 2010-06-28
Hey, this might be out of the scope of this forum,.. but I got a problem... I spent a month and a half building a website and this chuckle head I built it for can't pay up. Now he comes to me and says he can pay installments,.. It's a weird situation...

anyway,.. I got a back door to the sight working,.. but I wanna see if there is a way I can tie the files to an existing files so that if they try to delete the back door files the rest of the site no longer functions.

anyone know anything about this?

---

### Post by Ryan Dwyer on 2010-06-28
Why have you given them the code if they haven't paid for it?

Any change you make can be reverted by the customer if they know how. If you set up a frontend file to check for file existence of the backdoor file, the customer could just remove that check.

---

### Post by stderr on 2010-06-28
As Ryan states, if the client can find a backdoor he can find a backdoor 'protector'. It's simply levels on levels - security through obfuscation. It never works well, and this is before we consider the moral issues here.

But what would you use a backdoor to achieve anyway? It's a bit like a nuclear "deterrent" - there is simply no value in having it. Do you think you'd be paid further installments or otherwise achieve anything positive after disrupting the website? Trying to blackmail the client would be highly ill-advised.

To vaguely answer your question, there are most probably things that could be done to obfuscate the backdoor and make it terribly difficult and time-consuming to remove (such as could be discovered by taking hints from techniques employed in existing malicious pieces of code). But I don't think anyone here would recommend such action, in general or in this context, either from the perspective of satisfying your interests or the wider interest.

You have to remember that when somebody has physical access to a box, there's not very much you can do to control their access.

---

