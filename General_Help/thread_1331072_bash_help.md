---
title: "bash help"
date: 2009-11-18
forum: General Help
---

### Post by ryanfx on 2009-11-18
Hey everyone,  I had a quick question which I hope one of you should quickly be able to answer:

I have a file which has sets of data, line by line.  I need to be able to delete all characters between two sets of given 'key' characters such as the following:

```

Hi:  Blahlblah lblah::- @thisshouldgoaway@ tester!!!!

```

should result in

```

Hi:  Blahlblah lblah::- tester!!!!

```

however every line may or may not contain these key characters.  Is there an easy way to do this using the great tools sed + awk?  If so, could you grace me with the command?

---

### Post by ryanfx on 2009-11-19
I figured out my answer - 

```

sed 's/character.*character//g'

```

where character = whatever you want to delete between

---

