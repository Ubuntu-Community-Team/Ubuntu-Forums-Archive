---
title: "need to run commands from a .txt file"
date: 2011-09-06
forum: General Help
---

### Post by Arminius on 2011-09-06
maybe it's not ment to be a .txt file, I'm not sure
just want to fill a file with commands
then just call on that one text file from the command line, and it will just run that files contents in order.
I'm assuming that's possible?

---

### Post by haqking on 2011-09-06
> **Arminius said:**
> maybe it's not ment to be a .txt file, I'm not sure
just want to fill a file with commands
then just call on that one text file from the command line, and it will just run that files contents in order.
I'm assuming that's possible?


I think what you mean is like a batch file in windows which in Linux is Bash or Shell scripting.

See here [https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

and some youtube tutorials here [http://www.youtube.com/watch?v=DK3QnJs4wIE](http://www.youtube.com/watch?v=DK3QnJs4wIE)

---

### Post by nothingspecial on 2011-09-06
That would be a script

Put ```
#!/bin/bash
```

at the top, then your commands on a seperate line each or seperated with a ;

Put them in the order you want them run

Call the script something eg chocybar

Make it executable
```

chmod +x chocybar
```

and run it

```
./chocybar
```

Congratulations, you just wrote a script.

---

### Post by haqking on 2011-09-06
> **nothingspecial said:**
> That would be a script

Put ```
#!/bin/bash
```at the top, then your commands on a seperate line each or seperated with a ;

Put them in the order you want them run

Call the script something eg chocybar

Make it executable
```

chmod +x chocybar
```and run it

```
./chocybar
```Congratulations, you just wrote a script.


+1 

better explanation than mine ;-)

---

### Post by Frogs Hair on 2011-09-06
Are referring to an executable script ?  

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting) 

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by Arminius on 2011-09-06
> **nothingspecial said:**
> That would be a script

Put ```
#!/bin/bash
```

at the top, then your commands on a seperate line each or seperated with a ;

Put them in the order you want them run

Call the script something eg chocybar

Make it executable
```

chmod +x chocybar
```

and run it

```
./chocybar
```

Congratulations, you just wrote a script.

thanks, worked perfectly

---

### Post by sisco311 on 2011-09-06
> **haqking said:**
> 
See here [http://linuxconfig.org/Bash_scripting_Tutorial](http://linuxconfig.org/Bash_scripting_Tutorial)


OMG, that tutorial is horrible! I wouldn't recommend it for a beginner.



@OP try the BashGuide instead: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by haqking on 2011-09-06
> **sisco311 said:**
> OMG, that tutorial is horrible! I wouldn't recommend it for a beginner.



@OP try the BashGuide instead: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)


ha ha it is indeed, wrong link i meant [https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

which was posted after me i see.

will edit above ;-)

cheers

---

