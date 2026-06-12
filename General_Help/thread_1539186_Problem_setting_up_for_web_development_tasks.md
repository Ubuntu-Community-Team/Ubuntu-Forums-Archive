---
title: "Problem setting up for web development tasks"
date: 2010-07-26
forum: General Help
---

### Post by manObject on 2010-07-26
I am a refugee from Microsoft Windows and now need to use Ubuntu as a web development workstation instead. However, I seem to be missing the php scripting language.
The problem is, the Ubuntu Software Centre tool does not seem to list any suitable php package and the Installed Software tool does not list any such php package either (Apache http server is up and running but cannot serve php docs or execute php snippets in html docs).
I am using Ubuntu desktop edition 9.10 (I won't be using this as the live server; just for browsing localhost). Can anyone give me a clue as to how to proceed?

Many thanks in anticipation.

---

### Post by thebigob on 2010-07-26
from the command line try

```

sudo apt-get install php5

```

---

### Post by manObject on 2010-07-27
> **thebigob said:**
> from the command line try

```

sudo apt-get install php5

```
Thanks for your idea. It certainly works better than:

sudo yum install php5          # :))

I also found a marvellous command at [https://help.ubuntu.com/9.10/serverguide/C/installing-from-cd.html:](https://help.ubuntu.com/9.10/serverguide/C/installing-from-cd.html:)[B]

sudo tasksel install lamp-server[/B]

which pretty much set up everything I needed - including all the configuration so that apache, mysql and php work seamlessly together. Although the above command is aimed primarily at the Ubuntu Server build, it worked fine for my desktop option. I am much impressed!

---

