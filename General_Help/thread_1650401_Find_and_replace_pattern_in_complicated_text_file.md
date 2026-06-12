---
title: "Find and replace pattern in complicated text file"
date: 2010-12-21
forum: General Help
---

### Post by Pithikos on 2010-12-21
Here's a snippet of my text file:
```

| UnitEnteredLos()  ||  ||  ||  ||  unitID, teamID
|-
| UnitLeftRadar()  ||  ||  ||  ||  unitID, unitTeam
|-
| UnitLeftLos()  ||  ||  ||  ||  unitID, unitDefID, teamID

```How can I replace every function from the textfile so it becomes like this:
```

| [[/UnitEnteredLos()/]]  ||  ||  ||  ||  unitID, teamID
|-
| [[/UnitLeftRadar()/]]  ||  ||  ||  ||  unitID, unitTeam
|-
| [[/UnitLeftLos()/]]  ||  ||  ||  ||  unitID, unitDefID, teamID

```So I want each "functionName()" to become  "[[/functionName()/]]".

I have been using Gedit and I read the basics of regular expressions some time ago but can't remember much. Any suggestion is welcome.

---

### Post by V-Turn on 2010-12-21
> **Pithikos said:**
> Here's a snippet of my text file:
```

| UnitEnteredLos()  ||  ||  ||  ||  unitID, teamID
|-
| UnitLeftRadar()  ||  ||  ||  ||  unitID, unitTeam
|-
| UnitLeftLos()  ||  ||  ||  ||  unitID, unitDefID, teamID

```How can I replace every function from the textfile so it becomes like this:
```

| [[/UnitEnteredLos()/]]  ||  ||  ||  ||  unitID, teamID
|-
| [[/UnitLeftRadar()/]]  ||  ||  ||  ||  unitID, unitTeam
|-
| [[/UnitLeftLos()/]]  ||  ||  ||  ||  unitID, unitDefID, teamID

```So I want each "functionName()" to become  "[[/functionName()/]]".

I have been using Gedit and I read the basics of regular expressions some time ago but can't remember much. Any suggestion is welcome.

Here's a very useful site to test regexp live : [http://gskinner.com/RegExr/](http://gskinner.com/RegExr/)

The pattern your are looking for is (\w*\(\)). See [http://gskinner.com/RegExr/?2spah](http://gskinner.com/RegExr/?2spah) for your example live.

V.

---

### Post by Pithikos on 2010-12-21
> **V-Turn said:**
> Here's a very useful site to test regexp live : [http://gskinner.com/RegExr/](http://gskinner.com/RegExr/)

The pattern your are looking for is (\w*\(\)). See [http://gskinner.com/RegExr/?2spah](http://gskinner.com/RegExr/?2spah) for your example live.

V.

Thanks! Though I am not sure how I am supposed to use the expression to replace the text.. :-k

---

### Post by Pithikos on 2010-12-21
Problem solved.

I just used Geany (seems it beats the heck out of Gedit).
I just clicked on Seach>Replace and checked the "Use escape sequences"(it even has an option for regular expressions).

Then I replaced "\n| " with "\n| [[/"
and "()  ||" with "()/]]  ||".

Worked as a charm :cool:

---

