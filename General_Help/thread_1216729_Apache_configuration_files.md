---
title: "Apache configuration files"
date: 2009-07-18
forum: General Help
---

### Post by Belerophon on 2009-07-18
Hi.

I'm tying to understand apache2 configuration files. The thing is that I need to disable the the server identification in http responses.

So I decided to include the directive:
```
ServerTokens Prod
```

inside apache2.conf. 

This works as expected! 
But as I don't like to mess with the default config files, I decided to create a new config file inside /etc/apache2/conf.d/ and put there the code shown above.

However, this does not work, and apache continues to show it's version number!
Also, putting the same code inside http.conf does not work either!

But these files are included inside apache2.conf and should be read and it's directives applied! 

What's wrong in my approach?

---

### Post by Belerophon on 2009-07-18
I found the answer.

Unfortunately, in /etc/apache2/conf.d/ was already a file, named "security" which defined the directive:
```
ServerTokens Full
``` 

So, my config file must have been read first, and security file in last place. The directive was overridden by the last file!

My bad...

Thank you.

---

