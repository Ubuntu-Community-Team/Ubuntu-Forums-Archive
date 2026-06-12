---
title: "a question on bash script"
date: 2011-03-26
forum: General Help
---

### Post by volvolinux on 2011-03-26
Hello I am a linux beingeer. I am learning bash now. I have turned to this part several time , and I think the best way to learn it is to see how some programme's script mean. I met a part but don't know the menaing of this. coudl you please help?
 
from the script, the first is:
 
die()
{
local m="$1"
echo "$m" >&2
exit 1
}
 
what does this do?

---

### Post by sisco311 on 2011-03-26
```

# die is a function
die ()
{
# the value of the first positional parameter $1 
# (the first argument passed to the function) is 
# assigned to the local variable m.
  local m="$1"
# the value of m is printed to stderr
  echo "$m" >&2
# the script quits with exit status 1
  exit 1
}
```

See:
[http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)
[http://mywiki.wooledge.org/BashGuide/InputAndOutput](http://mywiki.wooledge.org/BashGuide/InputAndOutput)
[http://mywiki.wooledge.org/BashGuide/CompoundCommands](http://mywiki.wooledge.org/BashGuide/CompoundCommands)

---

### Post by volvolinux on 2011-03-26
thanks man.
I added your link to my favroutie folders. it is always pleasure hvae you here!

---

