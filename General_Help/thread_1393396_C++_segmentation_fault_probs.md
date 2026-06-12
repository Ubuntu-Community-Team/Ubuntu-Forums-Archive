---
title: "C++ segmentation fault probs"
date: 2010-01-29
forum: General Help
---

### Post by hariwonderful on 2010-01-29
Hey there everyone!
i am a new user trying out ubuntu for the first time and was very glad and excited to begin the journey, and i can compile many codes before...but one code compiled successfully but it didnt execute properly resulting in a segmentation fault.
here's the error:

> 
hari@ubuntu:~$ g++ bin_search.cpp
hari@ubuntu:~$ ./a.out
Enter the size of the 1D array:: 6
Enter the elements of the array:: 1 2 3 4 5 6
Enter the element to be searched:: 3
Segmentation fault
hari@ubuntu:~$ 
I am using Ubuntu 9.04 fully updated and kernel version 2.6.28.17
Here's the source code:

```

#include<iostream>
using namespace std;
int main()
{
    int a[50],i,n,end=n-1,beg=0,ele,mid;
    cout<<"Enter the size of the 1D array:: ";
    cin>>n;
    cout<<"Enter the elements of the array:: ";
    for(i=0;i<n;i++)
        cin>>a[i];
    cout<<"Enter the element to be searched:: ";
    cin>>ele;
    mid=(beg+end)/2;
    while((beg<end)&&(a[mid]!=ele))
    {
        if(ele<a[mid])
            end=mid-1;
        else
            beg=mid+1;
        mid=(beg+end)/2;
    }
    if(a[mid]=ele)
        cout<<"Element was found at:: "<<mid;
    else
        cout<<"Element was not found!";
    return 0;
}

```

---

### Post by c0mput3r_n3rD on 2010-01-29
```

#include<iostream>

using namespace std;

int main()
{
    int a[50];
    int size   = 0;
    int search = 0;
    int where  = 0;
    bool is_found = false;

    cout << "Enter the size of the 1D array:: ";
    cin  >> size;
    cout << "Enter the elements of the array:: ";
    for(int i = 0; i < size; i++)
        cin >> a[i];

    cout << "Enter the element to be searched:: ";
    cin  >> search;

    for(int i = 0; i != search; i++)
    {
    if(a[i] == search)
            is_found = true;
    where = a[i];
    }

    if(is_found)
        cout << "Element found at " << where << "!\n";
    else
        cout << "Element not found!";
    return 0;
}

```When you create a for loop, you must declare i as an int:
for(int i = 0; ... )

Also, make more useful names, and take a note to the standards of spacing for readability;  as you can see my code is much clearer and easier to read.

I almost forget, you were trying to use assignment as test statement.  "=" is not the same as "==".  That's probably where your error came from.

---

### Post by n0dix on 2010-01-29
mid is an integer and you use to keep a double, in this case:
```
mid=(beg+end)/2;
```
In your example, beg=0, and end = 5, the result is mid=2.5. I think this is the error. Change mid with type double.

---

### Post by c0mput3r_n3rD on 2010-01-29
> **n0dix said:**
> mid is an integer and you use to keep a double, in this case:
```
mid=(beg+end)/2;
```In your example, beg=0, and end = 5, the result is mid=2.5. I think this is the error. Change mid with type double.

Yes that's correct that is another issue I forgot the mention.  I don't believe that would be a segmentation fault because it just a logic issue as the decimal is just dropped and the integer value would just be 2.  It would not stop compile you just wouldn't get the right outcome half of the time.

---

### Post by n0dix on 2010-01-29
> **c0mput3r_n3rD said:**
> ```

#include<iostream>

using namespace std;

int main()
{
    int a[50];
    int size   = 0;
    int search = 0;
    int where  = 0;
    bool is_found = false;

    cout << "Enter the size of the 1D array:: ";
    cin  >> size;
    cout << "Enter the elements of the array:: ";
    for(int i = 0; i < size; i++)
        cin >> a[i];

    cout << "Enter the element to be searched:: ";
    cin  >> search;

    for(int i = 0; i != search; i++)
    {
    if(a[i] == search)
            is_found = true;
    where = a[i];
    }

    if(is_found)
        cout << "Element found at " << where << "!\n";
    else
        cout << "Element not found!";
    return 0;
}

```When you create a for loop, you must declare i as an int:
for(int i = 0; ... )

Also, make more useful names, and take a note to the standards of spacing for readability;  as you can see my code is much clearer and easier to read.

I almost forget, you were trying to use assignment as test statement.  "=" is not the same as "==".  That's probably where your error came from.


Hey, this code is more inefficient, because you do a search value by value. The code of hariwonderful is more fast, because do a search divide by two. See the link: [http://en.wikipedia.org/wiki/Binary_search](http://en.wikipedia.org/wiki/Binary_search)

---

### Post by c0mput3r_n3rD on 2010-01-29
> **n0dix said:**
> Hey, this code is more inefficient, because you do a search value by value. The code of hariwonderful is more fast, because do a search divide by two. See the link: [http://en.wikipedia.org/wiki/Binary_search](http://en.wikipedia.org/wiki/Binary_search)


Yes, it is more efficient, how ever it is more error prone, the original code was just wrong (no offense hariwonderful I'm not knocking you) and mine is a more simple algorithm.  You also have to remember that when you would be working with like 10 numbers it's not going to be more efficient, because 5 is not far from 0 and 10, whereas 500 is much farther than say 0 and 1000.  Technically, you're correct, but logically mine works the same as you would be doing just about the same (possible less) searches.  Nice catch!

---

### Post by n0dix on 2010-01-29
> **c0mput3r_n3rD said:**
> Yes, it is more efficient, how ever it is more error prone, the original code was just wrong (no offense hariwonderful I'm not knocking you) and mine is a more simple algorithm.  You also have to remember that when you would be working with like 10 numbers it's not going to be more efficient, because 5 is not far from 0 and 10, whereas 500 is much farther than say 0 and 1000.  Technically, you're correct, but logically mine works the same as you would be doing just about the same (possible less) searches.  Nice catch!

Yes you are right, but we don't know if hariwonderful need a binary search or a simple search. If it is not obligatory to use binary search it's better to use your code.

---

### Post by c0mput3r_n3rD on 2010-01-29
> **n0dix said:**
> Yes you are right, but we don't know if hariwonderful need a binary search or a simple search. If it is not obligatory to use binary search it's better to use your code.


Yes hariwonderful if that was a home work assignment and you had to do binary search don't use mine lol  It should be simple to modify the code I gave to do that though.  My algorithm is better, my algorithm with binary search, even better!

---

### Post by hariwonderful on 2010-01-30
Well I am really happy that all you people have taken time to help a newbie like me and I welcome your suggestions whole-heartedly. Sorry c0mput3r_n3rd but I cant use simple search...this code is Binary Search.
But any ways I'll implements your suggestion, the rough idea for the code was given by our Computer teacher, but I find him less reliable.
Thanks to you too n0dix!

I'll tell y'all as soon as I get it corrected.....:D

---

### Post by hariwonderful on 2010-01-30
Sorry it didn't work!
By changing mid value to float, it brought more errors as gcc doesn't accept 'void main()'
Guess I'll have to search another method

---

### Post by hariwonderful on 2010-01-30
I got it guys! My brother helped me find out that I had given end=n-1 in the beginning of the code...which gave mid a garbage value. The corrected code is:
```

#include<iostream>
using namespace std;
main()
{
    int n,end,beg=0,ele,mid,a[50];
    cout<<"Enter the size of the 1D array:: ";
    cin>>n;
    cout<<"Enter the elements of the array:: ";
    for(int i=0;i<n;i++){
        cin>>a[i];
    }
    [COLOR=Red]**end = n-1;**[/COLOR]
    cout<<"Enter the element to be searched:: ";
    cin>>ele;
    mid=(beg+end)/2;
    while((beg<end)&&(a[mid]!=ele))
    {
        if(ele<a[mid])
            end=mid-1;
        else
            beg=mid+1;
        mid=(beg+end)/2;
    }
    if(a[mid]==ele){
        cout<<"Element was found at:: "<<mid;
    } else {
        cout<<"Element was not found";
    }
    return 0;
}

```Thanks again.

---

### Post by pbrane on 2010-01-30
**Never mind then. I see that must have been a typo in the post.** Moving the assignment of *end* was the fix.

Have a look at this. It may be that you test in the last 'if' statement is incorrect.

```

#include<iostream>

using namespace std;

int main()
{
    int a[50], n, end=n-1, beg=0, ele, mid;
    
    cout << "Enter the size of the 1D array:: ";
    cin >> n;

    cout << "Enter the elements of the array:: ";
    for(int i=0; i < n; i++)
        cin >> a[i];

    cout << "Enter the element to be searched:: ";
    cin >> ele;

    int mid = (beg + end) / 2;
    while((beg < end) && (a[mid] != ele)) {
        if(ele < a[mid])
            end--;
        else
            beg++;
            
        mid = (beg + end) / 2;
    }

    if (a[mid] **==** ele)
        cout << "Element was found at: " << mid;
    else
        cout << "Element was not found!";
    return 0;
}

```

That operator should be a **==** not **=**. The way you have it you are trying to assign the value of *ele* to *a[mid]*

Using a float isn't going to work. The variables you are testing are *ints*, i. e. the array index.

---

