---
title: "Python help"
date: 2010-09-22
forum: General Help
---

### Post by olddai on 2010-09-22
Working from the Command Line/Terminal i have created a folder called 'my_examples' and in this folder i have placed a file called 'profile.py'. Could someone explain how i make this file executable and how to call it please. I have been told to type "chmod" but where do i type it please. Thanks all.

---

### Post by scandido on 2010-09-22
Firstly, you can call it through Python by moving to the my_examples directory and then typing

python profile.py

To make the file executable directly, add this as a first line

#!/usr/bin/python

which indicates to the system the script should be run using the interpreter in the folder /usr/bin/python and then mark the file itself as executable by typing

chmod u+x profile.py

You can replace the "u" with an "a" to indicate this should be an executable file for "All" vs. "current User". Of course, "profile.py" can be replaced with any valid path to your script, and you can add "my_examples" to your shell path to be able to execute the script by typing "profile.py" in any directory.

Good luck.

---

### Post by BobVila on 2010-09-22
> **olddai said:**
> Working from the Command Line/Terminal i have created a folder called 'my_examples' and in this folder i have placed a file called 'profile.py'. Could someone explain how i make this file executable and how to call it please. I have been told to type "chmod" but where do i type it please. Thanks all.

In your teminal, go to the my_examples directory.

Type ```
chmod 700 profile.py
```

You can then run the code by typing the following: ```
python profile.py
```
Alternatively, if you've added the following on the first line of your script: ```
#!/user/bin/env python
``` you can run it with: ```
./profile.py
```

---

### Post by Bachstelze on 2010-09-22
> **BobVila said:**
> 
Type ```
chmod 744 profile.py
```


Uh, no, this makes the file world-readable, which mightnot be wanted. The correct way is [font=monospace]chmod +x[/font].

---

### Post by BobVila on 2010-09-22
> **Bachstelze said:**
> Uh, no, this makes the file world-readable, which mightnot be wanted. The correct way is [font=monospace]chmod +x[/font].

Fair enough... just figured he had bigger fish to fry. I'll edit to 700.

---

