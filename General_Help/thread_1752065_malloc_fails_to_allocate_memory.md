---
title: "malloc fails to allocate memory"
date: 2011-05-07
forum: General Help
---

### Post by urrohit on 2011-05-07
hello guys .... I am developing a code where I need to store the planes of an object in a tree & also i need to store it in a list for further processing ... when I try to allocate using malloc the memory allocation 

when i checked this in internet , I came to know that it may because the memory that I am trying to allocate may be more than the size_t variable 

please help me out with this malloc problem

this is the piece of code :

these are the structures ```
struct dot
{
	int x;
	int y;
	int z;
};

struct polygon
{
	int d;
	struct dot p[4],equation;
};
	
struct plist
{
	struct polygon plane;
	struct plist *next;
};

struct tree
{
	struct polygon plane;
	struct tree *front,*back;
};

typedef struct dot point;
typedef struct polygon poly;
typedef struct plist list;
typedef struct tree bsp;
```

and this is where i get a segmentation fault because of the failure in allocating the memory
```
list * insert(list *li,poly p)
{
	list *new;
        new=(list *)malloc(sizeof(list));
	new->plane=copy(new->plane,p);
	new->next=NULL;
        .....
        .....
}

```

I get a segmentation fault at new->plane=copy(new_plane,p);

please help

---

### Post by r-senior on 2011-05-07
You should always test the return value of malloc to see if it is NULL and report the error:

```

struct plist *head;

if ((head = (struct plist *)malloc(sizeof(struct plist))) == NULL) {
        perror("insert:malloc");
        exit(EXIT_FAILURE);
}
...

```

Otherwise you end up in the situation you are in now - not really knowing what is happening. Assuming malloc() is not returning NULL though, that doesn't explain the segmentation fault. What's in your copy() function?

The other thing I'd say is that typedefs can make your code harder to read. I understand what you are trying to do, but it creates an extra layer of abstraction that the reader has to get through.

---

### Post by urrohit on 2011-05-07
thank you r-senior for your suggestions ...

but, is there any way by which i can ensure that the memory is allocated everytime i use malloc

---

### Post by r-senior on 2011-05-07
> **urrohit said:**
> but, is there any way by which i can ensure that the memory is allocated everytime i use malloc
No, you can't guarantee that. That's why you have to check for the possible error. The vast majority of the time it will work, but you need to check the pointer that it gives you. It will only return NULL in exceptional circumstances, e.g. all the memory and virtual memory is used, or you somehow asked for 0 bytes to be allocated.

I'd be very surprised if malloc was not returning a valid pointer in your case. Have you tried checking for a NULL return value and aborting? Does it abort? If not, the memory was allocated and your problem is elsewhere - in your copy() function I would guess.

---

### Post by urrohit on 2011-05-08
ya .. I checked the value of the of the pointer variable after allocation . Every time I compile and run it i get a NULL value 

does malloc allocate memory when the structure that we are using contains another structure (i.e, nesting of structure)

---

### Post by urrohit on 2011-05-10
thank u for suggestions .. i checked the code & it had some bugs now the code is working fine

---

