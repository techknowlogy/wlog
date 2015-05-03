---
layout: post
title: "Thought Experiments and a Goodbye Before the Vacation"
date: 2015-05-03 20:00:00
categories: activities
---

###Date: Apr 27, 2015, Wednesday###

###Place: IT Lab 6, ASE, Coimbatore###

**Plan for the session**:       

To introduce the different levels of thought and work between the inception of an idea and it's implementation, and to familiarise attendees with the computational thinking involved in the process.

**Tools/programs planned to use**:      

Heavy usage of the Python programming language for demonstrations, a couple of programs to demonstrate linking between thoughts and solutions on paper to those on the computer.


**The problem**:        

People who are generally afraid of programming and otherwise active in terms of visualising ideas and thoughts are afraid so because of a divide between the way they think naturally and the way the need to understand how a computer thinks[?]. A significant portion of beginners are taught programming with an emphasis on the syntactical working of a particular language. Due importance which must be given to the logical constructs and thought patterns is often found lacking. The aim of this session was to try and identify such symptoms and help have fun while thinking of ideas and programming.

```
Programming is not the goal, it can be an effective means to reach your goal, provided you learn to use your tools well.
```

Let's get to work:

Problem 1:

A basic problem requiring usage of the built-in [os](https://docs.python.org/2/library/os.html) module in python. The program involved reorganising files in a directory by renaming them according to some predefined rules. [Courtesy Udacity's course on Introductory Programming in Python for the idea](https://www.udacity.com/course/viewer#!/c-ud036/l-993460168/m-1015728603)

To start with, let's say I have a message for you. The message is in the form of photos (.jpg files) inside a directory, each photo carrying one letter, or a space, or a period.

Keep in mind that the photos in the directory are sorted by filenames. So, I've named all my files in the msg directory after names of cities. 

And to make things not so easy, I've scrambled the letters in the message by altering the filenames. Each filename has a random number prefix in front of the name of a city.

![Before execution of the program](https://github.com/techknowlogy/techknowlogy.github.io/raw/master/images/2015-05-03/before_exec.png)


The task in this problem was to rename all the files in a way that the random number prefixes are filtered, and the result is that the letters of the message are arranged in the order which was intended earlier.

![After execution of the program](https://github.com/techknowlogy/techknowlogy.github.io/raw/master/images/2015-05-03/after_exec.png)

No big funda here. The main purpose of the program was to get you acquainted with certain important functions and the program flow in python.

I asked the attendees to write their solution on paper first, and then code it.

I told them how I would write similar steps for making the problem in the first place.

{% highlight text %}
How I made the problem:
1.read message letter by letter. For each letter, the
following sequence of steps is followed:
1.1. from the "alphabet" folder, the letter is copied to
the "message" folder
1.2. the name of the copied file must be such that the
letter comes in its position according to the message.
1.3. for this a list of names can be taken in alphabetical
order and names can be assigned to files as they are copied
the message is ready in a form that is readable by the
viewer, we need to scramble the message

2.scrambling the message
well, I'll leave this for you to do :p
{% endhighlight %}

Anyway, the solution to the problem is a mere 10 lines of code

{% highlight python %}
import os

saved_path = os.getcwd()
path_to_message = os.path.join(saved_path,"msg")

file_list = os.listdir(path_to_message)
print file_list


os.chdir(path_to_message)

for file_name in file_list:
    os.rename(file_name, file_name.translate(None, '0123456789'))

os.chdir(saved_path)
{% endhighlight %}

Well, I haven't included comments on purpose, look up the functions with an internet search to learn about what they do.

We learnt quite some stuff from this relatively simple problem which will make thinking about the next one a little easier.

To make a list, we learnt:

>general python code structure

>some new functions

>>os.getcwd() [to get the location of the current working directory]

>>os.listdir(path) [to list the items in a given directory]

>>os.chdir(path) [to change to a given directory]

>>os.rename(src, dest)

>>and more

>using lists and loops in python

The problem we examined and solved after this was concerning management of photos and eliminating duplicates to save space. Not too complicated, but complicated enough to learn new things from. I'll write about that one soon.



###References:###

[Python documentation for the OS module](https://docs.python.org/2/library/os.html)

[Python documentation in general](https://docs.python.org/2)

[Programming Foundations in Python](https://www.udacity.com/course/viewer#!/c-ud036/l-993460168/m-1015728603), the online course on Udacity from which I got the photo-scrambling idea
