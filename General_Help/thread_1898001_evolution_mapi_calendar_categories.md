---
title: "evolution mapi calendar categories"
date: 2011-12-20
forum: General Help
---

### Post by b_g on 2011-12-20
Hello,

I've got a problem with evolution-mapi.

My evolution 3.2.1 is connected to exchange 2010 correctly, I can get new mails, contacts and some calendar events.

But if in my exchange, I have set a category to the event, it doesn't appear in evolution, and if I add a category in evolution I can't save it : I got an error 
*Cannot modify calendar object: Impossible to modify an element to the server: SetProps*: Erreur MAPI MAPI_E_CALL_FAILED (0x80004005)* (error message translated from french)

I guess categories have not been synchronized, but I don't know how to check this or how to force syncing. 
I don't even know how to get more verbosity for evolution. I started it in cli with --debug, but I don't get a lot of details in the file.

Regards,

-- 
b_g

---

### Post by metallica1973 on 2011-12-20
I feel you pain,

I have tried everything from evolution 3.2.1 using:

```

ii  evolution-exchange                       3.2.0-0ubuntu2                           Exchange plugin for the Evolution groupware suite

```

to thunderbird 3.X/ and lightening using:

```

http://gitorious.org/lightning-exchange-provider/pages/Home

```

to Davmail:

```

http://davmail.sourceforge.net/

``` 

and cannot get this piece of @#$!# to work. Davmail seems to be abit better of the options but if you dont know your paths to where the stuff is, it is useless. I will give you an update if I make progress. We just recently upgrade from exchange 2007 to 2010 to the pain has begun.

regards

---

