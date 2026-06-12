---
title: "Lynx: SSL error"
date: 2009-07-20
forum: General Help
---

### Post by mamboknave on 2009-07-20
I've this command line:

>> lynx -accept_all_cookies  "https://us.etrade.com/e/t/invest/quotesandresearch?content=3&sym=BAC"

Lynx starts properly but before opening the web page it asks: 

"SSL error:no issuer was found-Continue? (y)"

I'm clueless about this error. I answer Yes and the page opens properly. But...

I really need to avoid that question. Two options:

1. Fix somehow the SSL error - How?
2. make lynx to open that page disregarding the SSL error - is there such an option for the command line?

Hope someone can help... Thanks in advance.

---

### Post by dfreer on 2009-07-20
What happens when you remove the **s** from http**s**?

EDIT: Nevermind, I see it forces a redirect on you.

---

### Post by mamboknave on 2009-07-20
> **dfreer said:**
> What happens when you remove the **s** from http**s**?

That's not an option. That web page is https, not http.

---

