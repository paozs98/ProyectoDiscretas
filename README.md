# ProyectoDiscretas
Estudiantes:   Marcelo Esquivel Segura Wesly Rodolfo Segura Monge Juan Pablo Vargas González Paola Zúñiga Solís 

import   csv, timeit
import random

a = None

def timing_quicksort(start, stop, step):
    global a
    results = []
    population = list(range(0, stop))
    for n in range(start, stop, step):
        size = start + n
        a = random.sample(population, size)
        print("Size={}".format(size))
        tn = timeit.timeit("quicksort(a,0,len(a)-1)", number=500, globals=globals())
       
        results.append((size, tn))
    return results
	
  
//QuickSort tiempo

def quicksort_time_save(filename="info/quicksort.csv", start=10, stop=1000, step=100):
    results = timing_quicksort(start, stop, step)
    with open(filename, 'w', newline='') as csvfile:
        writer = csv.writer(csvfile, delimiter=';',quotechar='|', quoting=csv.QUOTE_MINIMAL)
        writer.writerow(['i', 'n', 'time(n)'])
        for i, (n, tn) in enumerate(results):
            writer.writerow([i, n, tn])



def quicksort(A,lo,hi):
	if lo < hi:
		pivot=random.choice(A)
		p = particion(A,lo,hi,pivot)
		quicksort (A, lo, p - 1)
		quicksort (A, p + 1, hi)
		
		
def particion(A,lo,hi,pivot):
	i=lo
	j=hi
	done = False
	while not done:
		while A[i] < pivot :
			i=i+1
		while A[j] > pivot:
			j=j-1
		if i>=j:
			return j
			done = True
		else:
			aux=A[i]
			A[i]=A[j]
			A[j]=aux
