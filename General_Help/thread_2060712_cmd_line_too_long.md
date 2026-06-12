---
title: "cmd line too long"
date: 2012-09-20
forum: General Help
---

### Post by kaykav on 2012-09-20
HI
      So how do I see the entire cmd if the cmd is very long?
            All I see is about the last half on my screen. I'm sure the full cmd is ready to invoke,but I can't see the full cmd.  Thank you

---

### Post by whatthefunk on 2012-09-20
It depedns on the terminal youre using.  You can probably either scroll over using the mouse or the right arrow key.

---

### Post by daslinkard on 2012-09-20
Interesting question you have here because as I write this I called up my terminal and it automatically wraps.  Could you be a little more specific exactly as to what situation you are referring to?  Is it when you are trying to copy a Command Line input?

---

### Post by Habitual on 2012-09-20
use the "\" character to "break up" long c-li commands...

example:
```
ec2-describe-snapshots -K /home/jj/.ssh/domain.com/pem/pk-OOPQ5MLZTVMPLIT63VC6DXGCNX6SFPH3.pem -C /home/jj/.ssh/domain.compem/cert-OOPQ5MLZTVMPLIT63VC6DXGCNX6SFPH3.pem --region us-west-1 | \egrep "vol-ad4f72ce|vol-794f721a|vol-654f7206" | sort -r -k 5
```could also be entered as:
```

ec2-describe-snapshots -K /home/jj/.ssh/domain.com/pem/pk-OOPQ5MLZTVMPLIT63VC6DXGCNX6SFPH3.pem \
-C /home/jj/.ssh/domain.com/pem/cert-OOPQ5MLZTVMPLIT63VC6DXGCNX6SFPH3.pem \
--region us-west-1 | \egrep "vol-ad4f72ce|vol-794f721a|vol-654f7206" | sort -r -k 5

```

Hope that helps...

---

### Post by oldos2er on 2012-09-21
Shift-PageUp, Shift-PageDown will scroll up and down in a console or terminal. Shift-End will take you back to the prompt.

---

### Post by dragonfly41 on 2012-09-21
To shorten commands you can try pre-defining long patterns as environment vars

e.g. in example [COLOR=Blue]ec2-describe-snapshots[/COLOR] command above 
[COLOR=Blue]
aws_snapshots = "ec2-describe-snapshots -K" 
aws_pk = "/home/jj/.ssh/domain.com/pem/pk-OOPQ5MLZTVMPLIT63VC6DXGCNX6SFPH3.pem"
aws_cert = "/home/jj/.ssh/domain.com/pem/cert-OOPQ5MLZTVMPLIT63VC6DXGCNX6SFPH3.pem"
aws_region = "--region us-west-1"
aws_vol = "vol-ad4f72ce|vol-794f721a|vol-654f7206"
aws_sort = "sort -r -k 5"[/COLOR]

then the shorter command becomes 
[COLOR=Blue]
$aws_snapshots $aws_pk $aws_cert $aws_region | \egrep $aws_vol | $aws_sort[/COLOR]

Or you could bundle vars together into shorter command strings.

---

### Post by kaykav on 2012-10-07
> **daslinkard said:**
> Interesting question you have here because as I write this I called up my terminal and it automatically wraps.  Could you be a little more specific exactly as to what situation you are referring to?  Is it when you are trying to copy a Command Line input?

Daslinkard;
    For instance;  I copied your reply , 47 words  , pasted it into my command line. This is what I get :
"re specific exactly as to what situation you are referring to? Is it when you are trying to copy a Command Line input?^Cld you be a little mo "
   Obviously not completely what you said. I don't know how to fix this problem. Maybe a plug-in?  Any suggestions?   Thank you

---

### Post by timsdeepsky on 2012-10-07
I am glad somebody posted this because i have been fighting the same problem for 3 days....I can not paste anything longer than 47 lines in my terminal....If i paste 50 lines,,,,it leaves 3 out,,etc....I have even re-installed ffmpeg,,,,changed the code around,,,etc....It does not matter if my terminal is full screen or smaller....Same limitations on 47 lines of code....Any input would be great....FYI,,,,the codes i am using now worked before with no issues....Thanks....

Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-31-generic
GNOME 3.4.2

---

### Post by timsdeepsky on 2012-10-07
Seems i can put the same long code in a bash script and call it from terminal and the script runs perfect....But putting the code in the terminal itself cuts off part of the code....

---

### Post by kaykav on 2012-10-07
> **timsdeepsky said:**
> I am glad somebody posted this because i have been fighting the same problem for 3 days....I can not paste anything longer than 47 lines in my terminal....If i paste 50 lines,,,,it leaves 3 out,,etc....I have even re-installed ffmpeg,,,,changed the code around,,,etc....It does not matter if my terminal is full screen or smaller....Same limitations on 47 lines of code....Any input would be great....FYI,,,,the codes i am using now worked before with no issues....Thanks....

Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-31-generic
GNOME 3.4.2

Ok It all has to do with the prompt code.
   for example  :   export PS1="\[\e[32;1m\]\w> \[\e[0m\]" will give you
  ~> (in green) , with the ability to word wrap. It does this with the 
       \[  and \]  in the code. See this url  [http://www.ibm.com/developerworks/linux/library/l-tip-prompt/](http://www.ibm.com/developerworks/linux/library/l-tip-prompt/). Hope it helps.

---

### Post by timsdeepsky on 2012-10-09
Well,,,,i still can not seem to figure out why my terminal is still limiting me....So i am just putting the code in a bash script and calling it with a url....Probably better off doing it this way anyway....I am moving on even though it is a 5 year LTS release....

---

