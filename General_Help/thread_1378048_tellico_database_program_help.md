---
title: "tellico database program help"
date: 2010-01-10
forum: General Help
---

### Post by trixman on 2010-01-10
i have a small question that i hope someone might be able to answer.
i am sorting some comics for my brother and we are using the program called "tellico"

the question we need help with is how can you put the comics in numerical order from lowest to highest in the program.

thanks to all

:popcorn:

---

### Post by wallaroo on 2010-01-11
Just to clarify, are you saying that you have sequentially numbered your collection and you want a way to include that number in the database so you can sort on it?

Or are you using an existing template field and just need to know how to sort on it?

---

### Post by trixman on 2010-01-11
> **wallaroo said:**
> Just to clarify, are you saying that you have sequentially numbered your collection and you want a way to include that number in the database so you can sort on it?

Or are you using an existing template field and just need to know how to sort on it?

thanks for the reply

what happend my brother had a list of comics  not in number order and put them into the tellico program. he then wanted to click a function button to place them in numerical order in one fast click.

the comics were not placed in the tellico program in number order. is there a way to sort them in the program in numerical order once the comics are in already.

thanks for the kind help
;)

---

### Post by wallaroo on 2010-01-11
Well here's where it gets confusing, the comicbook template doesn't have a numeric sequence field in it so there isn't a number to sort on. (at least the template I'm looking at).

If however you used an existing field (say 'Issue') then it's just a simple matter of right-clicking on the column headers row in the list view window and add the field containing the sequence number as a new column. Then click on that column header to sort the list in numeric order.

(But I suspect that you may not have a comic sequence number in your database).

---

### Post by trixman on 2010-01-11
> **wallaroo said:**
> Well here's where it gets confusing, the comicbook template doesn't have a numeric sequence field in it so there isn't a number to sort on. (at least the template I'm looking at).

If however you used an existing field (say 'Issue') then it's just a simple matter of right-clicking on the column headers row in the list view window and add the field containing the sequence number as a new column. Then click on that column header to sort the list in numeric order.

(But I suspect that you may not have a comic sequence number in your database).

nope i dont have that in my databse

---

### Post by wallaroo on 2010-01-11
OK, then I'll assume you want to add a sequence number field, but this means you will need to manually edit each existing comic record to fill in this field.

Step 1 - Call up the Field Editor:
- Click on 'Collection' then 'Collection Fields'.

Step 2 - Create the new field:
- Click on the 'New' button.
- Then enter a name in the 'Title' field, I would call this 'Comic Number'.
- Then select 'Number' in the 'Type' drop-down list.
- Leave 'Category' as 'General'.
- Give it a desciption such as 'Unique Comic Number'.
- Click 'Apply'.

The new field will be created at the bottom of the list, if you move it to the top of the list it will appear first in the edit boxes when you edit your records. 

- Press the 'up-arrow' button until the field appears at the top of the list.
- Click 'Apply' then 'OK'.

Step 3 - Add the field to the view window.
- Right Click on the column headers above the comic list (it probably just shows 'Title' at this stage).
- In the drop-down 'View Columns' list, select 'Comic Number' which should  add it to the column headers.
 
Step 3 - Add the sequence number to each record.
- Double-click on the first comic record to bring up the edit window - you can now enter its number in the new field.
- Click on the 'Save Entry' button then click the next record button (right arrow button) and repeat until all your Comic numbers have been entered.

You can now click on the Column header for 'Comic Number' to have the list ordered by number.

---

### Post by parys on 2010-01-13
The "Issue" field is intended to be used for the number of the issue. I think it's been a default field in the comic book collection for a while.

---

### Post by thedaylights on 2010-01-13
Sorry for the off-topic question, but does anyone know how to change the way tellico handles links to imdb? Right now it opens a new mail in Kompozer. I want it to open the link in Firefox.

---

### Post by parys on 2010-01-13
With KDE, you change the file association for text/html in the control panel. If you're using GNOME, I don't know. But Tellico just passes the link to the desktop environment to open, it doesn't choose the app itself.

---

### Post by thedaylights on 2010-01-14
I'm using Gnome. Not sure why it opens Kompozer though.

---

