---
title: "collect2: ld returned 1 exit status"
date: 2010-04-04
forum: General Help
---

### Post by Tapas Bose, India on 2010-04-04
I have written two file statistics.hpp where I declare the class and function and statistics.cpp where I define the functions, but when I am trying to compile it with test.cpp using command 
```
g++ test.cpp statistics.cpp -o test.o
```I am getting following error :
```
/tmp/ccVqvksi.o: In function `main':
test.cpp:(.text+0xfb): undefined reference to `double Stat::SimpleArithmeticMean<double>(std::vector<double, std::allocator<double> >)'
collect2: ld returned 1 exit status

```Please help.

---

### Post by gmargo on 2010-04-04
Very difficult to help if you don't post code.  (Don't post everything - just the absolute minimum example that demonstrates the problem.  Most of the time you will discover your bug just by trying to create that minimal example.)

My guess is that you don't have a function with the signature given in the error.  You're probably calling SimpleArithmeticMean with the wrong arguments.

---

### Post by Tapas Bose, India on 2010-04-04
Thank you for your reply.
This is my statistics.hpp :
```

#ifndef _STATISTICS_HPP_
#define _STATISTICS_HPP_

#include <vector>
#include <map>

using namespace std;

class Stat {
    public :
        Stat() { }
        
        template <typename DataType>
        DataType SimpleArithmeticMean(vector<DataType> );
        
        template <typename DataType1, typename DataType2>
        DataType1 WeightedArithmeticMean(multimap<DataType1, DataType2> );
};

#include "statistics.cpp"

#endif

```This is statistics.cpp :
```

#include "statistics.hpp"

template <typename DataType> 
DataType Stat :: SimpleArithmeticMean(vector<DataType> Collection) {
    DataType NoOfObservations = Collection.size();
    DataType SumOfSamples = 0;
    
    for (typename vector<DataType> :: iterator Iter = Collection.begin(); Iter != Collection.end(); Iter++) {
        SumOfSamples += *Iter;
    }
    
    DataType Mean = SumOfSamples / NoOfObservations;
    
    return Mean;
}

template <typename DataType1, typename DataType2>
DataType1 Stat :: WeightedArithmeticMean(multimap<DataType1, DataType2> Collection) {
    DataType1 NoOfObservations = 0;
    DataType2 SumOfSamples = 0;
        
    for (typename multimap<DataType1, DataType2> :: iterator Iter = Collection.begin(); Iter != Collection.end(); Iter++) {
        SumOfSamples += Iter->first * Iter->second;
        NoOfObservations += Iter->second;
    }

    DataType1 Mean = SumOfSamples / NoOfObservations;
    
    return Mean;    
}

```And it is simple_mean.cpp
```

#include "statistics.hpp"
#include <iostream>

using namespace std;

int main() {
    Stat ob;
    
    vector<double> vec;
    
    vec.push_back(42.5);
    vec.push_back(51.25);
    vec.push_back(50);
    vec.push_back(52);
    vec.push_back(44.25);
    vec.push_back(54);
    vec.push_back(54.97);
    
    cout << endl;
    cout << "  Mean : " << ob.SimpleArithmeticMean(vec) << endl << endl;
    return 0;
}

```But before I did not include statistics.cpp in the bottom of the statistics.hpp. Might that caused the error. Now it is okay. Here is the output :
```

tapas@My-Child:~/Programming/Statistics$ g++ -Wall simple_mean.cpp -o simple_mean.o
tapas@My-Child:~/Programming/Statistics$ ./simple_mean.o

  Mean : 49.8529


```Is procedure of including multiple file and compiling it okay? Can you suggest any better method to do so?
Thank you very much.

---

### Post by quicksilver30504 on 2010-04-04
Hi. I noticed you had a similar problem to me and resolved it. Could you please take a look at my thread? [http://ubuntuforums.org/showthread.php?p=9074847#post9074847](http://ubuntuforums.org/showthread.php?p=9074847#post9074847) Did you simply include the missing cpp file to fix this?

---

### Post by quicksilver30504 on 2010-04-04
Can you explain to me why this needs to be included at the end and why it does not work at the beginning?

---

