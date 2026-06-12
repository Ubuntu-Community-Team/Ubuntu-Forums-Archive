---
title: "Desktop Animations"
date: 2010-09-24
forum: General Help
---

### Post by lakerssuperman on 2010-09-24
Greetings,

While I am, and have been for the last six years, an Ubuntu user, I must admit my secret love for the look of the Mac.  Specifically the polish that is apparent in all areas of the system.  I would love to see Ubuntu reach that level of smoothness.  Here is my question, though we have Compiz for desktop effects, they are limited to windows and animating the movement and shape of those objects.  The one thing that stands out to me on Mac's is the use of subtle animation throughout the interface.  How hard would it be to have hardware accelerated effects for the entire interface;  things such as button presses and settings dialogs that animate in and out.

I don't want Ubuntu to become the Mac, I want it to continue to become it's own entity.  I love the new Radiance theme that comes with Meerkat.  The geek in me gets giddy thinking about that interface with smooth animations all over the interface.  Would it require a totally new technology, or a massive rewrite of the existing technologies?

---

### Post by Aaron5367 on 2010-09-24
I do believe that if you edit your compiz configuration (see ccsm) you can edit the various ways menus fade in and out, I think it's under "Animations". Other than that, search around for more plugins in the repos, there are gobs of things compiz can do.

---

### Post by lakerssuperman on 2010-09-24
Oh yes, I've played with tons of configurations, but none quite do what I want.  For example, when you are using iWork and select from the various templates, once you have clicked on the template you want, the icon for the template smoothly morphs into a new window containing your blank document.  That is kind of what I'm asking, does Compiz have the ability to do these things, or do these things fall under the realm of the GTK theme that is being used, and would there have to be Opengl rendering added to this aspect of the system?

---

### Post by Aaron5367 on 2010-09-24
That does indeed fall under GTK, which is far from being able to do that afaik. Yes, opengl would probably have to be involved.

---

### Post by lakerssuperman on 2010-09-24
That's what I was thinking.  That is something I would love to see Canonical and Ubuntu go after.  If Mark Shuttleworth is serious about matching Apple in the interface department this is something that I feel would be necessary, considering this type of animation is one of the pillars of the Apple interface.

---

### Post by lakerssuperman on 2010-09-24
I have read about Cairo rendering with Glitz.  Is this also an area that could be looked at for this functionality?

---

### Post by corncob on 2010-09-26
> **lakerssuperman said:**
> I have read about Cairo rendering with Glitz.  Is this also an area that could be looked at for this functionality?

Where did you read about this?

---

### Post by lakerssuperman on 2010-09-26
[http://cairographics.org/](http://cairographics.org/)

It seems though that this functionality was never followed through with.  According to this website, glitz has been depreciated and the new cairo-gl is what they are working with.

---

