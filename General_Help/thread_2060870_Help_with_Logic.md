---
title: "Help with Logic"
date: 2012-09-21
forum: General Help
---

### Post by Mohan1289 on 2012-09-21
Hey Guys i am currently doing the problems from [projecteuler.net]("http://projecteuler.net") as you guys suggested to improve my Programming Knowledge..

There i got a challenge 

The Problem is as follows

[COLOR="Red"]
The prime factors of 13195 are 5, 7, 13 and 29.

What is the largest prime factor of the number 600851475143 ?[/COLOR]

The Code/logic i wrote for that is as follows


import java.io.*;
import java.util.Scanner;
class prime 
{
	public static void main(String[] args) throws Exception
	{
		long i,j,a;
		long k=600851475143.;
		Scanner s =new Scanner(System.in);
		System.out.println("Enter Number");
		double num=s.nextDouble();
		System.out.println("Prime Number");
		for(i=1;i<num;i++)
		{
			for(j=2;j<i;j++)
			{
				if(i%j==0)
				{
					break;
				}
			}
			if(i==j)
			{
				if(i%k==0)
				{
					a=i;
				}
			}
		}
                   System.out.println(" "+a);
	}
}


Please tell me where my logic/code is messed up


Thank you..

As for me what i ave in mind is 

I want am checking all the prime numbers up to the given range i.e 600851475143

and then check each prime number, weather it's divisible or not with the given number.

Since it's in the for loop it will display every number that divides the given number.

But i need only the Largest Prime Factor which divides the given number....

So i placed the "println" statement out side the for loops. 

But it is showing me error, it says

The variable a may not be initialized...

Help me

---

### Post by shreepads on 2012-09-21
The variable 'a' is only set inside an 'if' clause, if that condition is not met you would be printing an uninitialised 'a' value, which is an error.

Which would happen if the input number were a prime number, in which case the largest prime factor would be the number itself.

So set a = num at the beginning...

Also, why do you need a pair of nested for loops, just one that goes from 2 to the square root of the num should be enough (with an additional variable to track the highest factor found so far)

---

### Post by Mohan1289 on 2012-09-21
> **shreepads said:**
> The variable 'a' is only set inside an '

Also, why do you need a pair of nested for loops, [COLOR="RoyalBlue"]"just one that goes from 2 to the square root of the num should be enough (with an additional variable to track the highest factor found so far)"[/COLOR]

Pardon Shreepad i don't get this part you mentioned... 

why i used two nested loops is to find the Prime numbers.

The Colored part is where i got confused

---

### Post by shreepads on 2012-09-21
> **Mohan1289 said:**
> Pardon Shreepad i don't get this part you mentioned... 

why i used two nested loops is to find the Prime numbers.

The Colored part is where i got confused

Sorry, what you're doing is correct, you need two nested loops with the given looping conditions...

---

### Post by Mohan1289 on 2012-09-21
Thank You Shreepad but can you tell why i am getting error???
If i assigned a=1 or something else at the starting does that solve the problem???

Even if i used long int the error is repeating itself.

---

### Post by shreepads on 2012-09-21
> **Mohan1289 said:**
> Thank You Shreepad but can you tell why i am getting error???
If i assigned a=1 or something else at the starting does that solve the problem???

Even if i used long int the error is repeating itself.

Assigning a=1 should solve the problem...

```
long i,j,a;
a = 1;
```

But to be correct you should assign a to the value 'num' (after converting double to long).

Issue is that you are printing the value 'a', possibly without having assigned it a value (because it is in an 'if' condition)...

---

### Post by Mohan1289 on 2012-09-21
Thank you i'll Try

---

