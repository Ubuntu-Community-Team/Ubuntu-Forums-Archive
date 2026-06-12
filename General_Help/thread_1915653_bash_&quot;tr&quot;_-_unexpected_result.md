---
title: "bash &quot;tr&quot; - unexpected result"
date: 2012-01-26
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-01-26
I ran this:

```
 tr [:blank:] [_] <'/media/ex3-WD-R6/script_testing_sandbox/dirty-string'> '/media/ex3-WD-R6/script_testing_sandbox/cleaned-string'
```and it changed this (note that the earlier spaces are spacebar spaces, but the last is a tab):
```
This Is String With    Blanks

```into this:
```
This_Is_String_With[Blanks

```rather than what I expected which was this:
```
This_Is_String_With_Blanks

```What did I do wrong?

And if there is a more appropriate forum for this sort of question, would you mind pointing me toward it?

Thank you if you can help.

---

### Post by Telengard C64 on 2012-01-26
Quote your meta-characters if you don't want the Bash to eat them.

---

### Post by papibe on 2012-01-26
I believe the brackets are reserve to make reference to special things, like blanks, for example. The character '_' does not fall in that category.

This should work:
```
tr "[:blank:]" "_" < input_file > output_file
```
Help it helps.
Regards.

---

### Post by Dreamer Fithp Apprentice on 2012-01-26
> **Telengard C64 said:**
> Quote your meta-characters if you don't want the Bash to eat them.


Thanks. Do you mean like this?:

```
tr [":blank:"] [_] <'/media/ex3-WD-R6/script_testing_sandbox/dirty-string'> '/media/ex3-WD-R6/script_testing_sandbox/cleaned-string' 
```It gives the same result.

Just to be clear, "dirty-string" is a pre-existing text file and "cleaned-string" is a text file created by this command.

---

### Post by Dreamer Fithp Apprentice on 2012-01-26
> **papibe said:**
> I believe the brackets are reserve to make reference to special things, like blanks, for example. The character '_' does not fall in that category.

This should work:
```
tr "[:blank:]" "_" < input_file > output_file
```Help it helps.
Regards.

Yep. That did it. Thanks. :)

---

