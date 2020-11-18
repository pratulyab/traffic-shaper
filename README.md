# Traffic Shaper using Token Bucker filter

<h2>Disclaimer</h2>
This repository is a placeholder for Traffic Shaper system which I have implemented as part of the graduate level course, CSCI 402 - Operating systems, which I have taken at USC (Spring 2020). The course instructor is Prof. Bill Cheng.

For more info about the course and instructor, see: http://merlot.usc.edu/william/usc/

Note: The actual repository, which contains the source code, has been made private so as to honour the code of conduct of the University. It will only be available to potential employers who want to assess my capabilities in similar domains (and also who will agree not to share it with anyone else too). If you want to look at the code, email me at: aditya.chandupatla@gmail.com

<h2>Brief description of the system</h2>
<p>This is a system developed entirely using C programming language by utilising low level constructs such as: POSIX threads, mutex, signals, dynamic memory using malloc/free, etc.</p>

<img src="tokenbucket.png" /><br/><span>Image Source: <a href="http://merlot.usc.edu/william/usc/">Course website</a></span><br/>

<p>There are two queues, one queue is responsible for incoming "packets", and the other queue serves as a waiting area for the packets which require "servicing" by the "servers". A packet moves from queue 1 to queue 2 only if the intermediate "Token bucket" has enough tokens requested by the incoming packet. If it moves, then the required number of tokens is deducted from the token bucket and the packet moves from queue 1 to queue 2. Otherwise, the packet waits at queue 1.</p>

<p>Furthermore, the Token Bucket receives tokens (i.e. simulated) at a predefined rate. The incoming packets come (i.e. simulated) either at a predefined rate, or a dynamic rate determined by specifying the inter-arrival-time between packets in an input file to the program. The token bucket also has a fixed size, which is practical, and if more tokens get generated, they are dropped.</p>

<p>Once the packet arrives at queue 2, it waits to be picked up by one of the two servers, which "process" (i.e. simulated) each packet for a specified amount of time (and the packet leaves the system).</p>

<p>Additionally, the system can receive a UNIX signal (in this implementation, it is SIGINT i.e. Ctrl+C), indicating the system to halt the simulation. The signal must be handled gracefully and all entities (packets, tokens, token bucket and servers) should terminate in a deterministic way.</p>

<p>Big challenge: All systems operate concurrently!</p>

<p>This basic construct is used widely in the Industry for throttling network traffic. Although, the real world scenario might be more nuanced, this implementation serves most of the basic-and-core needs of the system.</p>

<h2>Project Learnings, challenges and relevant concepts</h2>
<ul>
  <li>Multi-threaded system</li>
  <li>Race conditions</li>
  <li>Shared Data between threads</li>
  <li>Mutexes/Locks</li>
  <li>UNIX Signals</li>
  <li>Note: More details in the private repository</li>
</ul>
