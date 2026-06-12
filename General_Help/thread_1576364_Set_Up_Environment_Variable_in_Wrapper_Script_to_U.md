---
title: "Set Up Environment Variable in Wrapper Script to Use Helper Programs"
date: 2010-09-17
forum: General Help
---

### Post by tanggo81 on 2010-09-17
Greetings,
 
I am a newbie in using linux and have just recently compiled molden 4.9 ([http://www.cmbi.ru.nl/molden/molden.html](http://www.cmbi.ru.nl/molden/molden.html)) and tinker 5.1 ([http://dasher.wustl.edu/tinker](http://dasher.wustl.edu/tinker)) in my Ubuntu 9.10 system. The installation of moden requires users to create a wrapper script and set up the environment variables in order to use other helper programs, such as tinker (details can be found at [http://www.cmbi.ru.nl/molden/zmat/setup.html](http://www.cmbi.ru.nl/molden/zmat/setup.html))
 
My problem is that the molden program does not recognizes the environment variable for tinker and it does not executes the requested task (an error message appeared saying that environment variable TNK_ROOT not set, TNK_ROOT refering to the tinker directory). I wonder if the wrapper script has to be (in certain way) linked with the .bashrc file or molden executable file in order for the script or the environment variables in the script to be recognized by the program and hence execute the helper programs? If It is true, how can I do that?
 
Here are the codes that I used in the wrapper script:
 
```

#!/bin/csh
setenv TNK_ROOT /usr/bin/tinker
/usr/local/bin/gmolden.exe $argv

```
 
Could anyone please give me some suggestions?
 
Thank you very much in advance.

---

