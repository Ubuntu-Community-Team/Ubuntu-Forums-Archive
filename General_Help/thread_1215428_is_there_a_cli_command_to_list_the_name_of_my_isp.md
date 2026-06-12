---
title: "is there a cli command to list the name of my isp?"
date: 2009-07-17
forum: General Help
---

### Post by nickleus on 2009-07-17
or any other way to easily get the name of my isp?
i want to do something like this:
```
 lynx -dump http://slurpware.org | whois | grep "role:"
```but i just get the whois help text output
how would one write this correctly?

slurpware.org gives you only the ip address as output
then i want to pipe that ip address into whois
then grep only the line called "role:" (and as an added bonus, how would i exclude the text "role:" so i just get its value?)

---

### Post by jerrrys on 2009-07-17
this any help?

[http://www.whatismyip.com/tools/ip-address-lookup.asp](http://www.whatismyip.com/tools/ip-address-lookup.asp)

---

### Post by nickleus on 2009-07-17
> **jerrrys said:**
> this any help?
[http://www.whatismyip.com/tools/ip-address-lookup.asp](http://www.whatismyip.com/tools/ip-address-lookup.asp)
it's a start in the right direction, thanks. i would like to be able to do it from the command line though.

---

