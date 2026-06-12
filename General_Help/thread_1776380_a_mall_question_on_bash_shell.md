---
title: "a mall question on bash shell"
date: 2011-06-06
forum: General Help
---

### Post by volvolinux on 2011-06-06
Hello

I am trying to learn some script skills.

I have seen such a bash shell:


```

for x
do
        sed -f sedsrc $x > tmp.$x
done

```

then we can trigger the shell script from the command line:

./shell t1

My question is that it seems the "t1" will pass to the x in "for x".... I haven't seen any explanation in this behavior from Google. Can someone give me an answer?

---

### Post by DaithiF on 2011-06-06
Hi,
this behaviour is explained in **man bash**:

      for name [ [ in [ word ... ] ] ; ] do list ; done
              The  list  of  words following in is expanded, generating a
              list of items.  The variable name is set to each element of
              this  list in turn, and list is executed each time.  [B]If the
              in word is omitted, the for command executes list once  for
              each  positional  parameter  that  is  set [/B]

---

### Post by volvolinux on 2011-06-06
thanks, dude. Cool~! i will man them next time - -

---

