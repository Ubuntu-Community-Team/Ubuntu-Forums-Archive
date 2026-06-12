---
title: "emacs - change indentation preference"
date: 2010-05-02
forum: General Help
---

### Post by wotsit on 2010-05-02
Hi - this is an emacs question but relates to a programming language. It is however an emacs question, and not a question about programming, so I thought the post would best fit here.

When I code in java, I use emacs, there is one small yet annoying issue.

My code is formatted consistently with opening braces on a new line after declarations. Like this:

```
public class UserAuth
**{**
    Context initCtx = new InitialContext();
    Context envCtx = (Context) initCtx.lookup("java:comp/env");
    DataSource ds = (DataSource) envCtx.lookup("jdbc/users");
    
    public boolean returnDecision(String username, String password)
    **{**
```

When I press return and tab to get my brace in, emacs is too clever, and it shoots past the position the brace wants to be in. This is because some java programmers put the opening brace on the same line as the declaration, so emacs thinks, hey, I'll automatically indent to here, so that he is ready to go. If I were to format my code this way, this would be perfectly correct.

To rectify the problem, I press backspace to get the cursor lined up to the beginning of the declaration plus one line, and I press the brace key. The brace, instead of getting keyed where my cursor is, jumps 4 spaces, and gets keyed where my cursor originally overshot to. Again, it is trying to help, but it is ignoring the large minority of java programmers who format code with opening braces always on new lines.

I know I can change some behaviour with C-c C-o, but I don't know the arguments I have to provide it. so my question is, how do I tell it to only tab to the beginning of the declaration on the line above, and how do I tell it to put my brace where I want it without it second guessing me?

Sorry if it seems a bit of a 'matter of principle' question. Arguments over formatting code can get heated, and this is just the way I learned. Plus I think it looks a lot nicer.

---

