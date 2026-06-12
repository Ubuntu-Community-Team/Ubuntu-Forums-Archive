---
title: "How to create a custom command for the console?"
date: 2010-08-16
forum: General Help
---

### Post by ZequeZ on 2010-08-16
Hello, I was wondering how can I create a custom command for the console?
For example, I want to create a command called "phptime" that do the following: &#8220;php -r 'echo time()."\n";'&#8221;

I have to create a bash file and paste somewhere right? xD

---

### Post by ubun_two on 2010-08-16
1, Create a file called phptime

2, Open the file and enter:

> #!/bin/bash

php -r 'echo time()."\n";'


3, Save and close

4, Open Terminal and go to where the file is located

5, Type "chmod 755 phptime"

That should do it.

---

### Post by Vaphell on 2010-08-16
if it's a simple command you can add an alias to your .bashrc file

```

alias phptime='php -r 'echo time()."\n";''

```

every time you type in phptime, terminal silently replaces it with the actual command and executes. Probably there will be problem with parsing due to multiple ', you need to figure it out :-)

try
alias phptime='php -r "echo time().'\n';"'

---

### Post by ZequeZ on 2010-08-16
Thanks both of you ^^. Though the Vaphell solution it's faster :P.
(Btw: I think in the Vaphell method you have to use double quotes because if I use single quotes it gives an error :S)

---

### Post by SoFl W on 2010-08-16
You can add the alais in the ".bashrc" file and it will start every time.
For more complicated commands you can define a function in your ".bashrc" file.

function somecommand { 
   cd /var/log/
   ls -la
   cd /etc
   ls -la
   cd /home/username
   ls -la
   }

---

