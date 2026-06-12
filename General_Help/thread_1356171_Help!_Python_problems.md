---
title: "Help! Python problems"
date: 2009-12-15
forum: General Help
---

### Post by HalpMe on 2009-12-15
Hey Guys, I have a test tomorrow and this question is going to be dead similar to my test question, and I'm a mech.E major but for some damned reason Python is a mandatory course for us. Please if any one could solve this I would be very grateful. Please Help me.
_______X__X_X_X_X_X_X_X_X_X_X__X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X_X__X_X_X_X_X_X_X_X__X_X_X_X_X_X_X__X_X_X_XX_X_X_


A family unit consists of one guardian and zero or more babies.
A baby has a name and an age.
Define classes for family unit and baby. (You will get more points if you make the data members private.)

All the family unit data are stored in a file named familiartxt. You are guaranteed that this file exists.
In the data file, a family unit is stored on at least one line - the guardian. After the guardian (well actually just the name) there are lines for each baby – their name and their age in parentheses.

Here is a sample data file showing the internal format of the data:

[COLOR="red"]Ralph The Magnificent Mangler
Quizzlechomps (32)
Miki (24)
END REC
Mary the Meek
Middendorf (812)
Muddle (10)
Makrryrlr (232)
END REC
Buster
END REC[/COLOR]

Write a function that will return a container of all the family units from this file. The file should be opened and closed in this function.
Write a function to display all the family units in a list of family units in descending alphabetical order by guardian..
Babies must be in the order of youngest to oldest. (This is not necessarily the order they are in in the file.

Finish Part ONE before going on to Part TWO


Part TWO --- Adding and removing babies.
Anyone who has a valid password can change things. A valid password here, is really in the range [33.55] or (457.993].
For now, be infinitely patient with the password entry
Once validated, they can choose to remove a guardian or a baby - but only one at a time – their password will have to validated after each change..

A family unit is chosen at random. The user decides to remove a guardian or a baby. If they choose baby, a random baby under the chose guardian's care is chosen. If they choose a guardian, all the babies under that guardian are also gone.

One of the rules of this world is that no guardians can be removed if their name is the same as a baby under another guardian. Your code must enforce this – just ignore any attempt in this case.

For processing"
Display all the family units and then go through the process of letting people validate their passwords and make changes.
Be sure to show all the family units after each person removes someone.

It's also possible that someone might decide to change the name of a guardian instead of removing them. When a guardian's name is changed, all of the baby under his care have their names changed to the new name also.
 
There is a special password that allows anyone who knows it to stop processing. When this happens, the number of babies still in the system is displayed (and then the program ends).
 

Here is a sample run of Part TWO. Remember to solve problems, not examples.
We are using the data shown above to start with.

[COLOR="Red"] 
Ralph The Magnificent Mangler
1.) Miki (24)
2.) Quizzlechomps (32)
Mary the Meek
1.) Makrryrlr (232)
2.) Middendorf (812)
3.) Muddle (10)
Buster
[no babies]

Enter password
3
Sorry, try again:
44
Which to delete – Guardian or Baby?
baby

Ralph The Magnificent Mangler
1.) Miki (24)
2.) Quizzlechomps (32)
Mary the Meek
1.) Makrryrlr (232)
2.) Muddle (10)
Buster
[no babies]


Enter password
900
Which to delete – Guardian or Baby?
guardian
Would you rather rename?
y
What's the new name?
Bizzy

 
Mary the Meek
1.) Makrryrlr (232)
2.) Muddle (10)
Buster
[no babies]
Bizzy
1.) Bizzy (24)
2.) Bizzy (32)

Enter password
STOP THIS MESS!

4 babies left[/COLOR]

---

