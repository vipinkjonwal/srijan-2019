Large Primes How to check them???

“God may not play dice with the universe, but something strange is going on with the prime numbers.”
-Paul Erdos
“December 21, 2018 -- The Great Internet Mersenne Prime Search (GIMPS) has discovered the largest known prime number, 282,589,933-1, having 24,862,048 digits. A computer volunteered by Patrick Laroche from Ocala, Florida made the find on December 7, 2018.”[1]
Primes, whole numbers with two factors, have always influenced the mathematical world with its beauty. It has made cryptography an enigma. Large primes are used in encryption to make networks more secure. And who can forget the million-dollar problem of Riemann Hypothesis, which is based on distribution of primes. Also, there is a sort of joy in finding the large prime numbers in the society.
The layman’s way for checking a number to be prime is, trial division of the number n with 2,3 and odd numbers of the form 6k±1 (k>=1) less than or equal to √n. But time complexity for executing this is exponential (O(2√n)) to the size of n and is not acceptable for large numbers. Let’s take a try, if we assume that in one second 1016 iterations executes on super computer and we run this program for 24x7x365,  it would not have completed till the moment, even if we started at the big-bang to check the primality of largest prime known till date.
The question is, how the primality of a numbers with such a huge size is checked? 
Some methods like using Fermat’s Little Theorem and Miller-Rabin test exists, but there is some error/probability associated with them.
Lucas-Lehmer test, developed by Édouard Lucas and improved by him and Derrick Henry Lehmer[2] is used to check the primality of special types of numbers known as Mersenne numbers. These are the numbers of the form 2n – 1. Under this test, a Mersenne number, 2n -1 is prime, if and only if, n is odd prime and (n-1)th element of the Lucas-Lehmer series (given below) is divisible by the number. 
The Lucas-Lehmer series is given as –
		L(i) = 4,		i = 1
		L(i) = (L(i-1))2 – 2,	i > 1
It grows very fast, first few elements of the series are 4, 14, 194, 37634, 1416317954,.…. So, instead of first calculating the (n-1)th element of the series and then checking it’s divisibility. We keep on passing just the remainders from ith iteration to (i+1)th, which makes calculation somewhat fast.
Let’s check the primality of 27-1.
27-1 = 127, n = 7
L(1)=4
Incrementing till L(6) by taking remainders from one iteration to next.
4 mod 127 = 4								…L(1)
42-2 mod 127 = 14 mod 127 = 14					…L(2)
142-2 mod 127 = 194 mod 127 = 67					…L(3)
672-2 mod 127 = 4487 mod 127 = 42					…L(4)
422-2 mod 127 = 1762 mod 127 = 111					…L(5)
1112-2 mod 127 = 12319 mod 127 = 0					…L(6)
As L(6) mod 127 equals zero. 127 is a prime number.
This is the main idea behind the construction of GIMPS’s algorithm, which is generally used to find large mersenne primes. GIMPS gives thousands of dollars as prize money for finding large primes to the enthusiasts.
An algorithm for primality checking of all types of numbers is also of theoretical interest known as AKS primality test, founded by IIT Kanpur’s professors named Manindra Agrawal, Neeraj Kayal and Nitin Saxena, in 2002[3]. It is generalization of Fermat’s Little Theorem’s polynomial. It states that a number n is prime if all the coefficients of polynomial (x - 1)n - (xn - 1) are divisible by n. This algorithm runs in polynomial time with size of n. AKS’s correctness is based on generalized Riemann Hypothesis. It is not much used in practical as other fast algorithms also exists which works on a particular type of number.

Some amusing facts :
The largest prime found without using computer is, 117*(2148+1) (a Proth number)by Aime Ferrier. He used mechanical calculator and Proth’s theorem for this.[4]
The largest prime checked just by hand calculations is 2127-1 by Lucas. Using his Lucas-Lehmar series.
It is difficult (but scientifically possible) to remember all the digits of the largest prime known till date in decimal by humans. But you may remember it in binary ;)



References--
[1]https://www.mersenne.org/
 [2]The Largest Known Prime by Year: A Brief History
[3] Agrawal, Manindra; Kayal, Neeraj; Saxena, Nitin (2004). "PRIMES is in P”.  Annals of Mathematics. 160 (2): 781–793. doi:10.4007/annals.2004.160.781. JSTOR 3597229.
[4]Hardy, G. H. and Wright, E. M. An Introduction to the Theory of Numbers, 5th ed. Oxford, England: Clarendon Press, pp. 16-22, 1979.
