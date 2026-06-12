---
title: "Minimising buttons moved left without my consent"
date: 2011-01-19
forum: General Help
---

### Post by jesuisbenjamin on 2011-01-19
Hello there,

Today my minimising, maximising, and closing buttons on the window border moved from the right to the left without any apparent reason. (At least i dind't ask them to).  The other computer I work on didn't change though.

I use Gnome, Dust Sand theme on 10.04.

I really dislike having them there, how can i move them back where they belong?


Thanks.
B.

---

### Post by Foxheadz on 2011-01-19
Well I don't know of any command but you can do it using ubuntu tweak

---

### Post by Foxheadz on 2011-01-19
I don't know of any command but you can change it using ubuntu tweak

---

### Post by jesuisbenjamin on 2011-01-19
Mhh. Ok. I appreciate the help but: how is it i need a program to set something back, which has changed without that program?

I mean do you see my point here? Isn't what just happened odd, and shouldn't it be as easy to fix by finding the cause?

---

### Post by ronnielsen1 on 2011-01-19
To switch it back 

  [INDENT]   Press Alt+F2, then type gconf-editor   and press enter. That’s for opening   the configuration editor.
      Once on this editor, in the item tree   at the left, you have to look for this   path  app -> metacity -> general and   you doubleclick on the field named    button_layout.
      Then, you have only to change the   value field and put this:
      menu:minimize,maximize,close
 [/INDENT]

---

### Post by Foxheadz on 2011-01-19
Well ubuntu tweak is just a gui for various commands. So there is a bash command for it but it's way easier to use ubuntu tweak and it's a good tool to have. Sorry bout the double post it claimed i hadn't posted

---

### Post by jesuisbenjamin on 2011-01-19
@Ronnielsen: Thanks, good one :)
@Foxheadz: Thanks, i didn't know Tweak was just a mere frontend. No worries about the double post, it just happened to me as well :)

I just wonder how the configuration changed by itself though :-k

---

### Post by mick222 on 2011-01-19
The buttons have been on the left for a while now did you do a distribution upgrade

---

### Post by jesuisbenjamin on 2011-01-19
Nope, actually i am on 10.10 since it was released. Did updates and nothing more. As i said, the other computer i use still has the buttons on the right hand side.

(PS: what's the left thing anyway?)

---

### Post by tgm4883 on 2011-01-19
> **jesuisbenjamin said:**
> Nope, actually i am on 10.10 since it was released. Did updates and nothing more. As i said, the other computer i use still has the buttons on the right hand side.

(PS: what's the left thing anyway?)

It's a design/usability decision. Once you get use to it you'll find it makes more sense.

---

### Post by WorMzy on 2011-01-19
Mark Shuttleworth decided that something called "[Windicators]("http://www.markshuttleworth.com/archives/333")" should go on the right-side of the screen.

I dunno what happened to that idea. Possibly it's still in development.

Personally, I prefer having the buttons on the right side. I doubt Windicators would be available on Emerald themes anyway, so you'd have to use Metacity. :X

---

### Post by jesuisbenjamin on 2011-01-19
> **tgm4883 said:**
> It's a design/usability decision. Once you get use to it you'll find it makes more sense.

Well i tried the left-side buttons in 9.10 and 10.04 and found that it didn't make sense to me. At least it's not the way i intuitively use a computer.

Perhaps it has to do with writing from left to right, opening a book in a left-right fashion too. Besides i am right handed, so I want my buttons on the right hand side.

The good news is: Ubuntu allows to customise the interface. Fair enough.

Another point is the decision has been taken today on my computer, without my consent. That somehow upset me and i believe it would upset other users in such situation too.

It's like you'd get into your car and suddenly you'd find the wheel on the passenger side. I guess you know what I trying to say here.

Thanks for the info though.
B.

---

### Post by 3rdalbum on 2011-01-19
If you changed the theme to Ambiance or Radiance, it would also change the window buttons because this layout is attached to the whole theme. It's possible to select Ambiance/Radiance and then "Customise" the theme to look like Dust Sand but with the left buttons.

Otherwise, the buttons should only change on dist-upgrade from 9.10 to 10.04.

---

### Post by Splat_NJ on 2011-01-19
Any theme change will move the buttons back to the default left-side of the windows. That's been my experience every single time I've changed a theme or something within a theme.

---

### Post by jesuisbenjamin on 2011-01-19
What i don't understand now is why your default seems to be left-hand side layout, while my default is a right-hand side layout? I didn't tweak the Sand Dust theme of 10.10 except for changing the font to *sans*.

---

### Post by tgm4883 on 2011-01-20
> **jesuisbenjamin said:**
> Well i tried the left-side buttons in 9.10 and 10.04 and found that it didn't make sense to me. At least it's not the way i intuitively use a computer.

Perhaps it has to do with writing from left to right, opening a book in a left-right fashion too. Besides i am right handed, so I want my buttons on the right hand side.

The good news is: Ubuntu allows to customise the interface. Fair enough.

Another point is the decision has been taken today on my computer, without my consent. That somehow upset me and i believe it would upset other users in such situation too.

It's like you'd get into your car and suddenly you'd find the wheel on the passenger side. I guess you know what I trying to say here.

Thanks for the info though.
B.

I'm from Oregon, USA, so for all purposes I go left to right as well. When I close/minimize a program, my next stop is to either shut the computer down (top right), or more frequently, it is to open a new program (top left). The distance between closing a program and opening a new one if far greater with the buttons on the right.

As for it automatically doing it, it was an update to your theme. If you expect things to not change with updates, then don't do updates. The car analogy doesn't work unless you say "get the newest model of my car" then come back and find the steering wheel on the passenger side. The newest model comes with it on the other side, so how can you be upset about the change when you told it to update?

---

### Post by jesuisbenjamin on 2011-01-20
duplicate post.

---

### Post by jesuisbenjamin on 2011-01-20
> **tgm4883 said:**
> 
As for it automatically doing it, it was an update to your theme. If you expect things to not change with updates, then don't do updates. The car analogy doesn't work unless you say "get the newest model of my car" then come back and find the steering wheel on the passenger side. The newest model comes with it on the other side, so how can you be upset about the change when you told it to update?

I don't believe that a change of appearance in the interface defines as an update. Had i upgraded to a newer version Ubuntu, it wouldn't have come to me as a surprise.
I am just a modest user and provide feedback: _this experience was unpleasant and showed inconsistency_. Also I believe the Ubuntu logos below your name mean you are supposed to take note of this feedback, but if you prefer to be adamant and patronising instead, that is your choice.

---

### Post by tgm4883 on 2011-01-20
> **jesuisbenjamin said:**
> I don't believe that a change of appearance in the interface defines as an update. Had i upgraded to a newer version Ubuntu, it wouldn't have come to me as a surprise.
I am just a modest user and provide feedback: _this experience was unpleasant and showed inconsistency_. **Also I believe the Ubuntu logos below your name mean you are supposed to take note of this feedback, but if you prefer to be adamant and patronising instead, that is your choice.**

Nope, it means I'm a Ubuntu member, as are 500+ other people. Doesn't mean that I have to take note of anything. You updated a package, the theme package. Whether you like it or not, an interface change is the same as any other fix in Ubuntu. It's just more noticeable. 

In either case, it's fixed by a simple setting swap. So no real harm done.

---

### Post by mick222 on 2011-01-21
It doesn't bother ma one way or the other the only thing is some apps done obey the rules bbc "iplayer" for one.

---

