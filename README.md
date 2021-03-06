Fitness Evaluator Project
-------------------------

Tech Stack Used
---------------- 
Java 8

How to run
-----------
 - Add this project to eclipse with Java 8 as the JDK 
 - Run the CreateDataAndRun class which is the main class
 - Output will be printed on console
 
 Input/Output
 ------------
 - The input is prepared in CreateDataAndRun class and is the exact same input as provided in the challenge
 - The output is prepared in FulfillmentService.java, lines 34-37
 
 Algorithm 
 ---------
 1. The problem statement was to achieve the minimum sets of location-destination combinations
 2. To achieve the desired output, the best way ahead was to fulfill an order to the max using the best fit warehouse
 3. If the order is not fulfilled completely then move to the next fit warehouse
 4. The best fit warehouse has to be chosen based on how good it is to fulfill the order based on order items and their quantities
 5. Warehouses are sorted in best fit order
 6. Order will be first fulfilled using warehouses sorted on their best fit as calculated above
 
 Code Explanation
 ----------------
 - Data structure chosen for order is Order.java
 - Data structure for Warehouse is Warehouse.java
 - The above data structures are in strict coherence to the given problem statement
 - The data is created in the class CreateDataAndRun and it calls fulfill method of the FulfillmentService class by passing the orders and the warehouses
 - Orders are iterated and each order is passed along with the list of warehouses to the calculateFitness method
 - calculateFitness method iterates over each warehouse and sends the order and warehouse to calculateFitnessOfWarehouseForOrder
 - calculateFitnessOfWarehouseForOrder calculates the percentage of the order fulfilled by the particular warehouse and updates the perecentFulfilled attribute in Warehouse class
 - The warehouses are then sorted based on descending order of percentFulfilled
 - The order along with the sorted warehouse is then passed to the fillOrder method
 - fillOrder method fulfills the order and updates the warehouse inventory along with population of the FulfillmentData object which is used to display the output
 
 Assumptions
 -----------
 1. The input/output has been prepared in strict accordance to the problem statement
 2. Factors such as distance between location and destination, priority of location etc. have been kept out as there was no mention of them in the problem statement
 3. The code assumes that the input orders are already collated for particular locations
 4. The code assumes that it will fulfill the orders regardless of whether they get fulfilled fully or partially
 5. The code does not use any database or data repository, it creates data on the fly and prepares the output for display
 
 How to do this in Hybris
 ------------------------
 Doing this in Hybris will not require any kind of customization. It will work out of the box with just configurations as Hybris provides the support of Fitness Evaluator in warehousing extension. To try this out perform the following steps
 
 1. Install the latest Hybris B2C accelerator along with the oms module
 2. Open backoffice and click on "Sourcing Configuration" under Order Management
 3. Double Click on the default "Hybris_OMS_Config", it will open up the respective SourcingConfig
 4. Hybris by default provides 4 weight factors - distance, allocation, priority and source
 5. Mark the "Allocation Weight Factor" as 100, rest all as 0.
 6. This will make sure that whenever an order is fulfilled the best suited warehouse to fulfill that order completely is picked, hence reducing the number of destination-location combinations over time
