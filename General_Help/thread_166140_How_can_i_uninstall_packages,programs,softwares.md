---
title: "How can i uninstall packages,programs,softwares?"
date: 2006-04-25
forum: General Help
---

### Post by Anilkumar on 2006-04-25
Hello everybody

Thanks for the support here. I have a question here.

How can i uninstall packages,programs,softwares?

---

### Post by mjm115 on 2006-04-25
Take a look [here]("http://monkeyblog.org/ubuntu/installing.html").  This is a very well written article.

---

### Post by enopepsoo on 2006-04-25
I think it might help to add that you shouldn't really ever have to go outside of the synaptic universe, since there is an app in there to do almost everything.
I realize some things aren't in the yet (i.e. Automatix), but for any actual software there should be something in there that does the task you need.

With that being said I think that was a really cool article, and very thorough as well.

---

### Post by tsrjzq on 2006-04-25
just apt-get remove xxx, it's ok

---

### Post by Toxicity999 on 2006-04-26
sudo apt-get remove xyz
or just run synnaptic search for what you want to toss right click the icon to the left then 'Uninstall' (Remove?) The njust apply, either way.

---

### Post by Ramses de Norre on 2006-04-26
```
sudo apt-get remove --purge package_name
```
will delete the config files also (better if you wont be reinstalling the app)

---

