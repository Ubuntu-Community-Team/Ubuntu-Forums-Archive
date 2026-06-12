---
title: "Script to kill firefox-bin"
date: 2011-11-19
forum: General Help
---

### Post by ktechman on 2011-11-19
Is there any possible way to write a script to kill firefox-bin upon closing Firefox?

Thank for any reply

Ktechman

---

### Post by raja.genupula on 2011-11-19
actually  pkill <proces_name>

will kills that process , try that once.

---

### Post by haqking on 2011-11-19
[http://support.mozilla.com/en-US/questions/666158#answer-26223](http://support.mozilla.com/en-US/questions/666158#answer-26223)

[http://support.mozilla.com/en-US/questions/885957](http://support.mozilla.com/en-US/questions/885957)

there are plenty of others

---

### Post by ktechman on 2011-11-21
Is ther any way to avoid typing > killall firefox-bin  after closing Firefox with a simple script????

---

### Post by haqking on 2011-11-21
> **ktechman said:**
> Is ther any way to avoid typing  after closing Firefox with a simple script????

yes put it in a script.

However have you read the links above, you havent said if you tried any of the solutions and if they didnt work and what happened etc

---

### Post by ktechman on 2011-11-21
What would the script look like and where would I insert it?

---

### Post by haqking on 2011-11-21
> **ktechman said:**
> What would the script look like and where would I insert it?

it would look like:

```
killall firefox-bin
```

in a script ;-)

```
#!/bin/bash
killall firefox-bin
```

and save it, make it executable and stick it on your desktop.

However once again you never answered my question, have you tried the above solutions and none of them work ?

---

### Post by dgb-sinaga on 2011-11-22
To automatise the killing of firefox-bin, I open the firefox starting script 
 $ sudo gedit /usr/bin/firefox
then I wrote in the 2nd line  the command :  **pkill firefox-bin**
That 's all and its work since 2 days

---

### Post by ktechman on 2011-11-24
Both solutions that were mentioned:

> [http://support.mozilla.com/en-US/que...8#answer-26223](http://support.mozilla.com/en-US/que...8#answer-26223)

[http://support.mozilla.com/en-US/questions/885957](http://support.mozilla.com/en-US/questions/885957) I did try but with no joy.

so your saying that if use the:

> #!/bin/bash
killall firefox-bin

name it like 'CloseFirefox'

make it executable something like: 

> sudo chmod x CloseFirefox

how would you word the code to execute the script 'upon closing firefox execute CloseFirefox'????

---

