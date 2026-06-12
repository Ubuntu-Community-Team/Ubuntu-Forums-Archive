---
title: "Which Licence to choose?"
date: 2010-12-09
forum: General Help
---

### Post by Rishav Thakker on 2010-12-09
Hey guys. I really didn't find a category to post this so posted in general. Sorry if its wrong.

So I'm creating a facebook-uploader for nautilus (a nautilus-script) which would allow u to upload photos to facebook.

The thing is that my application is registered on facebook with a unique ID and SECRET (like username + password) and i have to use those to upload to facebook. It also generates an AUTHORIZATION CODE per person who uses the application (this is done via facebook).

So, for my application to work, I need to store the ID and SECRET in the source code, so that it can get the AUTHORIZATION CODE for the user, in order to post.

And if i make my source code visible to everyone, it would be a great security issue (due to the falling of ID and SECRET in wrong hands)

So far I've thought of the following options (source code is going to be in python):
1) make into an executable using cx-freeze
2) distribute .pyc (thats ruled out due to availability of 'decompilation'

So my question is which License should I choose? as under the GPL, I'd have to reveal the source code..

Any help would be really appreciated. Thanks guys :)

---

### Post by amauk on 2010-12-09
I don't use facebook, so this may be a stupid question, but why would other people use your login credentials?
everyone has their own accounts don't they?

---

### Post by Rishav Thakker on 2010-12-09
> **amauk said:**
> I don't use facebook, so this may be a stupid question, but why would other people use your login credentials?
everyone has their own accounts don't they?

No no. They're not MY login credentials. they're my application's credentials.
It goes like this:

1. My application is recognized by its credentials (so basically, any code sent to facebook via curl, containing my app's credentials would be recognized by facebook as my application)

2. the user is directed to a link containing my app's credentials
It looks something like [http://graph.facebook.com/?client_id=XXXX](http://graph.facebook.com/?client_id=XXXX) (not exact, but u get the point. XXXX is my ID) There he/she has to authorize my application, and my app gets a authorization code

3. My app uses that authorization code to post on behalf of that user.

---

### Post by amauk on 2010-12-09
This can't be the right way to do things with facebook
have you contacted them and asked what the process is for applications communicating with facebook?

Open or closed source makes no difference
you can extract any stored string from a binary

---

### Post by Rishav Thakker on 2010-12-09
Uhm I guess..
I went to the facebook developers section, and read the complete documentation (except for the how-tos on what my app will not do).

Mine's under the 'desktop applications'. Check it out:
[http://developers.facebook.com/docs](http://developers.facebook.com/docs)
[http://developers.facebook.com/docs/api](http://developers.facebook.com/docs/api)

I'll be using the 'graph' API.

---

### Post by amauk on 2010-12-09
Just to elaborate
A C++ program

```
#include <iostream>
#include <string>

int main()
{
	std::string foo = "Hello, this is a string";
	std::string bar = "Another string";

	return 0;
}
```

save that as, say foo.cpp, and compile
```
g++ -o foo foo.cpp
```

Then run the binary through strings
```
cat foo | strings | less
```
See the text plain as day

If you store a secret string in a program, you're screwed. Open/closed source doesn't matter

---

### Post by Rishav Thakker on 2010-12-09
oh ok.
So isn't there any way I can get my prog to have access to the secret string without actually storing it?
for eg what if i generate a string while execution?

something like this:

#include <iostream>
int main()
{
    std::cout << (char)54;
}

it doesn't store the character with ASCII numbering 54, but still displays it. So in that case, will it be accessible after creation of the binary?

And thanks for the info so far :)

---

### Post by amauk on 2010-12-09
Not going to work

Why do you think DRM on software / DVDs / etc. always fails

You have to ship the "key" along with the content
and anyone who looks for it can find the key

As I said,
this /cannot/ be the way facebook wants you to do things (unless they're completely retarded)
Contact them and ask

---

### Post by Rishav Thakker on 2010-12-09
Okayy.
Thanks a lot btw :) I was wondering about this since quite sometime back :)

So I guess I'll let it be for now, since even the online flash uploader has a patch :P If I have the time, I'll go more into the authorization details with facebook.

Although it was fun to upload stuff via the terminal :)

Thanks again.

---

### Post by Slim Odds on 2010-12-09
> **amauk said:**
> ...

Why do you think DRM on software / DVDs / etc. always fails

You have to ship the "key" along with the content
and anyone who looks for it can find the key

...


I was also going to mention this. They find all kinds of ways to try to hide it, but it's got to be there. Which is a fail!

---

