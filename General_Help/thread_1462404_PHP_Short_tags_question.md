---
title: "PHP Short tags question"
date: 2010-04-25
forum: General Help
---

### Post by Twizzle on 2010-04-25
I have Ubuntu server 9.10 installed with LAMP.

I have previously had both Zoneminder and Munin installed and both have worked at the same time.

I have just re installed everything and Zoneminder works. When I try to open the Munin site, I get:

[PHP]Parse error: syntax error, unexpected T_STRING in /var/www/munin/index.html  on line 1[/PHP]

Having done some reading, I understand that this is something to do with Zoneminder using short PHP tags where as Munin needs long(?) ones.

I can edit the php.ini file and change:

[PHP]short_open_tag = On[/PHP]

to off and Munin works....but Zoneminder does not.

I have no idea how I managed to get both working together last time.

There is mention of the authore of Zoneminder haveing a script that changes all short tags to long tags but again I can't get that to work. (It keeps telling me it cant find a file).

Is it possible / advisable to change this by hand in Zoneminder or can I do something the Munin to make it work?

---

### Post by jbiggs12 on 2010-04-25
Hi Twizzle,

Could you show us some of the code so that we could have a better idea of how to debug it? How are you introducing your PHP code?

---

### Post by Serpher on 2010-04-25
Open your PHP tags like this

<?php

Instead of just the plain '<?'. Good PHP scripts should have this regardless as that's the way it was intended to be and short tags was probably just influenced by some ASP noobs.

---

