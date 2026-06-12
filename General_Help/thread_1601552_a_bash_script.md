---
title: "a bash script"
date: 2010-10-20
forum: General Help
---

### Post by Ko$ on 2010-10-20
that runs a program N times, takes the numbers program produces (each time different) and calculates the average of those numbers.

I need it. Could someone help me, please?

---

### Post by DaithiF on 2010-10-20
something like:

```
#!/bin/bash
for (( i=0; i<[COLOR=Red]10[/COLOR]; i++ ))
do
  result=$([COLOR=Red]./someprog[/COLOR])
  total=$(( total + result ))
done
avg=$(echo "[COLOR=Red]scale=2[/COLOR];$total / $i" | bc)

echo "Average of $i executions is $avg"
```replace the bits in [COLOR=Red]red[/COLOR] to your requirements.

---

### Post by Ko$ on 2010-10-20
> **DaithiF said:**
> something like:

```
#!/bin/bash
for (( i=0; i<[COLOR=Red]10[/COLOR]; i++ ))
do
  result=$([COLOR=Red]./someprog[/COLOR])
  total=$(( total + result ))
done
avg=$(echo "[COLOR=Red]scale=2[/COLOR];$total / $i" | bc)

echo "Average of $i executions is $avg"
```replace the bits in [COLOR=Red]red[/COLOR] to your requirements.

Thank you very much.

---

