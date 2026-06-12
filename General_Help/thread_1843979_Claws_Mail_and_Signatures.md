---
title: "Claws Mail and Signatures"
date: 2011-09-14
forum: General Help
---

### Post by Th3Professor on 2011-09-14
In Gmail, I'm able to set the replies to insert my signature after the new message that I am writing, and it places the previous message (that I'm replying to) below my message and my signature.

In Claws mail, I am using templates to provide a consistent format for replies & forwards. However, the signature is getting thrown in at the bottom of the entire email, after my new message and even after the reply-to message. That's a horrible place for it.

I am using %X to plug in my new message before the reply-to/forwarded message. I'm using commands like %N, %A, %s, and %d for the from/subject/date info from the previous message, and I'm using %q for the actual content of that previous message.

I thought that %X would've included my signature with my new message. It does not.

How do I make Claws mail insert the signature after my new message but **before** the reply-to/forwarded message?

Thanks!

---

### Post by Th3Professor on 2011-09-14
Nevermind. I'm switching to another email client.

---

### Post by andybotA1 on 2011-11-08
I'd like to be able to use claws too, but this problem is a deal-breaker. ANYone? Is there a solution, any magic code for the templates?

edit: nevermind, I looked a little further and figured out how to edit the templates. My apologies for propagating this noob question. I also discovered the ire that is directed towards top-posters by da geeks.
Cheers!

---

### Post by andybotA1 on 2011-11-08
@Th3professor: use the symbol "%as" to insert the "account signature," plus turn off automatically inserting signature...

---

