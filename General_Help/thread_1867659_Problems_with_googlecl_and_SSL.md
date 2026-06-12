---
title: "Problems with googlecl and SSL"
date: 2011-10-23
forum: General Help
---

### Post by carl.davis on 2011-10-23
Hello,

I am trying to upload a document via googlecl and get an SSL warning. I posted an issue to the project but its status got changed to "Works for Me" and haven't received any further assistance.

When I execute 

```
cdavis@ubuntu-laptop:~/Desktop$ google docs upload reinstatement.pdf
``` 

It returns
```
Loading reinstatement.pdf
Failed to upload reinstatement.pdf: Server responded with: 403, <errors xmlns='http://schemas.google.com/g/2005'><error><domain>GData</domain><code>ServiceForbiddenException</code><internalReason>403.4 SSL required</internalReason></error></errors>
You may have to specify a format with --format. Try --format=txt

```

I have tried using the $PYTHONPATH variable and downloaded python-gdata 2.0.14 and 2.0.15 with the same results. I have tried to sym link /usr/share/pyshared/gdata and /usr/share/pyshared/atom to downloaded copiy of python-gdata 2.0.15 with the same results. I have also downloaded the latest googlecl and launched with 

```
./google docs upload /home/cdavis/Desktop/reinstatement.pdf
```

and received the same results. 

Hopefully someone that reads this has seen this issue and knows how to fix it.

Thanks,
Carl

---

