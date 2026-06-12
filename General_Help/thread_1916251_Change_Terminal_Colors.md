---
title: "Change Terminal Colors?"
date: 2012-01-27
forum: General Help
---

### Post by TheAJGman on 2012-01-27
I am making a small script and would like to know how I would change the background, the output text color, and the working directory.

---

### Post by WasMeHere on 2012-01-27
Hi TheAJGman,

You can use ANSI signals according to the following link
[[COLOR="RoyalBlue"]_http://en.wikipedia.org/wiki/ANSI_escape_code_[/COLOR]]("http://en.wikipedia.org/wiki/ANSI_escape_code")

Have fun finding out :-)
Olle

Edit: change the working directory with the cd command
```
cd 'where-you-want-to-go'
```

---

### Post by WasMeHere on 2012-01-27
... and two simple examples using ANSI.

So after
```
alias redtext='echo -e "\0033[31m"'
alias reset='echo -e "\0033[0m"'
```
try
```
redtext
```
```
reset
```

---

### Post by TheAJGman on 2012-01-27
Could I have an example? I can usually figure it out from there.
EDIT: ninja'd

---

### Post by TheAJGman on 2012-01-27
> **Olle Wiklund said:**
> ... and two simple examples using ANSI.

So after
```
alias redtext='echo -e "\0033[31m"'
alias reset='echo -e "\0033[0m"'
```
try
```
redtext
```
```
reset
```
How would I go about changing the  background or the blinking cursor.

---

### Post by WasMeHere on 2012-01-27
> **TheAJGman said:**
> How would I go about changing the  background or the blinking cursor.
Do as I did to get 'ESC', '\0033'
and select the sequence from the ANSI table in the link.

Blinking cursor speed is set with 5 and 6. 40-47 sets the background colour for example
```
alias cyanbg='echo -e "\0033[46m"'
```

---

### Post by TheAJGman on 2012-01-27
I meant how would I change cursor color. And that command doesn't change the background color for me

---

### Post by WasMeHere on 2012-01-27
> **TheAJGman said:**
> I meant how would I change cursor color. And that command doesn't change the background color for me

Well it creates an alias, so run the command
```
cyanbg
``` It works for me at least in gnome-terminal and xterm in Ubuntu 10.04 LTS. What is your version?

---

### Post by TheAJGman on 2012-01-27
I know what the alias is I just run the actual command in terminal to test it. I'm running oneiric.

---

### Post by WasMeHere on 2012-01-27
If you change the text colour and the background color, the cursor will get the text colour. Test with [FONT="Courier New"]redtext[/FONT] and [FONT="Courier New"]cyanbg[/FONT]

---

### Post by TheAJGman on 2012-01-27
I'm testing the commands directly by entering ```
alias redtext='echo -e "\0033[31m"'
```strait into the terminal and it doesn't change the cursor or the background of the terminal, it does change the background of the text.

---

### Post by WasMeHere on 2012-01-27
> **TheAJGman said:**
> I'm testing the commands directly by entering ```
alias redtext='echo -e "\0033[31m"'
```strait into the terminal and it doesn't change the cursor or the background of the terminal, it does change the background of the text.
[FONT="Courier New"]redtext[/FONT] changes the colour of the text
[FONT="Courier New"]cyanbg[/FONT] changes the colour of the background
and together they change the colour of the cursor
It can be reset to the default colours by [FONT="Courier New"]reset[/FONT]
There might be a difference, such that ANSI background colouring is not implemented in your version of Ubuntu, but have another try before giving up :-)

Edit: Now I understand: Yes, you have to write the whole window to change the background colour with this method. It can be done by cls[FONT="Courier New"][/FONT] 'clear screen'
```
alias cls='echo -e "\0033[2J"'
```

---

### Post by TheAJGman on 2012-01-27
I want to change the background color of the TERMINAL not the text.
Could any one with oneiric help me?

---

### Post by WasMeHere on 2012-01-27
> **TheAJGman said:**
> I want to change the background color of the TERMINAL not the text.

I edited the previous post: Use the [FONT="Courier New"]cls[/FONT] alias!

---

### Post by TheAJGman on 2012-01-27
Umm, that does nothing.

---

### Post by WasMeHere on 2012-01-27
> **TheAJGman said:**
> Umm, that does nothing.
If you use it directly:
```
echo -e "\0033[2J"
```

---

### Post by TheAJGman on 2012-01-27
it just skips a line as if you only typed echo

---

### Post by sudodus on 2012-01-27
Maybe it is confusing using alias. Just

- set colour and background
```
echo -e "\0033[31;46m"
echo -e "\0033[2J"
```
- reset
```
echo -e "\0033[0m"
```
to show what to include into a script from the examples in the previous posts.

Edit: Maybe you need the full path to the program [FONT="Courier New"]**/bin/echo**[/FONT] (to avoid a built-in command in your shell)

---

### Post by TheAJGman on 2012-01-27
That worked. Alias isn't confusing I use it all the time to shorten some of the larger commands.

---

### Post by WasMeHere on 2012-01-27
> **sudodus said:**
> Maybe it is confusing using alias. Just

- set colour and background
```
echo -e "\0033[31;46m"
echo -e "\0033[2J"
```
- reset
```
echo -e "\0033[0m"
```
to show what to include into a script from the examples in the previous posts.

Edit: Maybe you need the full path to the program [FONT="Courier New"]**/bin/echo**[/FONT] (to avoid a built-in command in your shell)
Thanks Sudodus for making it simpler :-)

And yes, maybe it needs to be /bin/echo

---

### Post by TheAJGman on 2012-01-27
Ok quick question, what would the orange text on black background be?

---

### Post by WasMeHere on 2012-01-27
TheAJGman,

I guess you finish your task on your own to get the colours you want for text, cursor and background. And when you are satisfied, please mark this thread SOLVED

Have fun :-)
Olle

---

### Post by TheAJGman on 2012-01-27
thanks everyone
wait how do i mark solved?

---

### Post by WasMeHere on 2012-01-27
I just saw you asked about colours: Have a look at the link to the wiki page about ANSI escape code. There are only a few colours implemented this way. I think you will get the colour according to the column of ***xterm***, so there is no orange. To get orange you need to do something else (depending of what terminal program you are using).

In gnome-terminal, you have the menu entry

Edit -- Settings -- Colours

Probably it can be set also via terminal commands, but I don't know how. If you can find out where the information is stored (in which file), you should be able to edit that file automatically.

---

### Post by WasMeHere on 2012-01-27
> **TheAJGman said:**
> thanks everyone
wait how do i mark solved?
Look at the top of the page, click on [COLOR="Red"]**Thread tools**[/COLOR] and select from the menu.

---

