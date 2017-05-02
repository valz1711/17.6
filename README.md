# 17.6
1 Uses of counters:
  Counters allow a developer to track aggregated events from all of those separate instances. 
  Counters act as an efficient mechanism for tracking the occurrences of global events within the map and reduces the phases of jobs. 
  The output of these Counters can be found in the job details of the Job Tracker web UI.


2 MRUnit testing
MRUnit testing framework is based on JUnit and it can test Map Reduce programs written on 0.20 0.23.x , 1.0.x , 2.x version of Hadoop.

3 Testing is useful because 
The Hadoop job might run for hours and then fail. Mostly, you need to debug the code, re-compile the logic and re-run it again. 
So testing is done on a small data.

4 
Task counter
Task counters gather information about tasks over the course of their execution, and the results are aggregated over all the tasks in a job. For example, the MAP_INPUT_RECORDS counter counts the input records read by each map task and aggregates over all map tasks in a job, so that the final figure is the total number of input records for the whole job.
File system counter
File system counters track 2 main details , number of bytes read by the file system and number of bytes written.
Job counter
Job counters are maintained by the jobtracker (or application master in YARN), so they don’t need to be sent across the network, unlike all other counters, including user-defined ones. They measure job-level statistics, not values that change while a task is running. For example, TOTAL_LAUNCHED_MAPS counts the number of map tasks that were launched over the course of a job (including ones that failed).

5 Raw comparator vs Writable Comparable
Raw comparator is faster as compared to Writable Comparable. Keys are compared using their corresponding raw bytes.
Writable Comparable is Slow as compared to Raw comparator.

6 Partitioner, Sort comparator, Group comparator
Partitioner
A partitioner works like a condition in processing an input dataset. The partition phase takes place after the Map phase and before the Reduce phase. The number of partitioners is equal to the number of reducers. A partitioner will divide the data according to the number of reducers. Therefore, the data passed from a single partitioner is processed by a single Reducer. HashPartitioner is the default partitioner in Hadoop, which creates one Reduce task for each unique “key”.  All the values with the same key goes to the same instance of your reducer, in a single call to the reduce function.
Sort Comparator
SortComparator decides how keys will be sorted in input of reduce. By default it uses natural ordering.
Group Comparator
Group Comparator decides which map output keys will be united (grouped) into one key, and of course all collections of values will be grouped too. Usually it takes a first key as the only one for summary collection.
