---
title: "bash scripting, how to enter input to a c++ program?"
date: 2012-02-24
forum: General Help
---

### Post by test_tube_baby on 2012-02-24
Hello,

I am using a bash script to run a cpp program several times. However, the program asks for user input. I want this input to be automated by the bash script.

How do I do that? I tried echo but echo doesn't work until the program has finished executing.

How do I allow bash to write an input when the cpp program prompts for one?

Thanks.

---

### Post by Thorsen V on 2012-02-24
doesn't redirection work?

$ myprog < some.txt

---

### Post by test_tube_baby on 2012-02-24
> **Thorsen V said:**
> doesn't redirection work?

$ myprog < some.txt
It works! thanks.

What if my program asks for several inputs? Does a new line in the .txt file mean a new input?

---

### Post by Thorsen V on 2012-02-24
> **test_tube_baby said:**
> It works! thanks.

What if my program asks for several inputs? Does a new line in the .txt file mean a new input?
It depends what you're using in your program but the answer is probably yes :)

---

