---
title: "Shell script bug?"
date: 2011-02-04
forum: General Help
---

### Post by worldsayshi on 2011-02-04
If it's not a bug it at least succeeds in bugging me. I write this in a shell script:

```
#!/bin/sh
S1="$1"
S2="abc"
if [ $S1!=$S2 ];
then
        echo "S1('$S1') is not equal to S2('$S2')"
fi
``` 

When running it by calling:
```
./myscript abc
```

I get:
```
S1('abc') is not equal to S2('abc')
```

How does that make sense?? I've tried some variations like not using '"' here and there but with no positive result.

---

### Post by Vaphell on 2011-02-04
mandatory spaces separating parts of whole condition

[php]if [ "$S1" != "$S2" ];
then
        echo "S1('$S1') is not equal to S2('$S2')"
else
        echo "S1('$S1') is equal to S2('$S2')"
fi
[/php]

---

