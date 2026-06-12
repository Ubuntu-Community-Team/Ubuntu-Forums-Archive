---
title: "Evolution quits when configuring MS exchange server"
date: 2010-07-14
forum: General Help
---

### Post by isopod on 2010-07-14
Hello all. I am relatively new to Ubuntu having installed it in January 2010 and made the update to 10.04. I am in an MS Windows workplace with MS Exchange Server 2003. I am trying to get evolution to check my email via the web based access (as I think it is not possible otherwise) and I did manage to get this to work for a week with the old version before I upgraded to 10.04 but I cannot get it to work again.

Steps leading to problem:
1) setup Evolution identifying myself email etc - click forward no problems
2) select Microsoft Exchange as server
3) username: johndoe
4) owa url: [https://webmail.blah.blah.blah.ca/](https://webmail.blah.blah.blah.ca/), I have tried both secured and plaintext password
5) click autheticate and put in password - evolution quits.

It always quits at this point. I am not sure why it suddenly worked before with karmic koala just before I upgraded to lucid because it did not work in karmic for the first few months either.

Any help would be appreciated

Thanks,
Dan

---

### Post by philinux on 2010-07-14
> **isopod said:**
> Hello all. I am relatively new to Ubuntu having installed it in January 2010 and made the update to 10.04. I am in an MS Windows workplace with MS Exchange Server 2003. I am trying to get evolution to check my email via the web based access (as I think it is not possible otherwise) and I did manage to get this to work for a week with the old version before I upgraded to 10.04 but I cannot get it to work again.

Steps leading to problem:
1) setup Evolution identifying myself email etc - click forward no problems
2) select Microsoft Exchange as server
3) username: johndoe
4) owa url: [URL] I have tried both secured and plaintext password
5) click autheticate and put in password - evolution quits.

It always quits at this point. I am not sure why it suddenly worked before with karmic koala just before I upgraded to lucid because it did not work in karmic for the first few months either.

Any help would be appreciated

Thanks,
Dan
http://live.gnome.org/Evolution/FAQ#Evolution_Exchange_.28formerly_known_as_Connector.29

---

### Post by isopod on 2010-07-14
> **philinux said:**
> http://live.gnome.org/Evolution/FAQ#Evolution_Exchange_.28formerly_known_as_Connector.29

Thanks very much Phil but I am sorry  that I cannot find a solution there. In fact I have the exchange server option and can enter my username (with or without the domain and using a backslash) and https address at the OWA box but the problem comes when I try to authenticate: I put in my password press enter and Evolution instantly quits, i.e. it does not appear to be trying to connect to anything and there are no error messages.

I have read of others having authentication problems and possibly that Evolution tries to change https to http but even if this were the case it should take a moment to try to connect then get an error but Evolution does not appear to be doing that.

I appreciate any  help - perhaps I am just doing something completely silly.

Dan

---

### Post by philinux on 2010-07-14
run evo from a terminal and see if it spits out an error when it crashes.

---

### Post by isopod on 2010-07-15
Thanks Phil. Here is the error message when I run from a terminal window

EI: MAIL PREFSSegmentation fault

Dan

---

