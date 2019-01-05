# SIGHZY
nosql assignment

//CREATE//

db.createcollection("courses")
db.courses.insert({
 course: "java",  
   details: {  
        duration: "6 months",  
        Trainer: "Sona jaiswal",
        Bacth :30
        category: "Programming language"
   {  
      Course: ".Net",  
        details: { Duration: "6 months",
        Trainer: "Prashant Verma" },  
        Batch:  20,
        category: "Programming Language"  
      },  
  })
  
  
  //READ//
  
  db.courses.find({
  Course: ".Net"
  })

 //UPDATE//
 >db.courses.update({'course':'java'},{$set:{'course':'advance java'}})
 
 >>>>>to check updated item<<<<<<<<
 
 >db.courses.find()  
 
 //DELETE//
 db.courses.remove( { type : "programming language" } )  
 
 ///FIND USING QUERIES//
 
 1-SELECT ALL DB-db.courses.find()  
 2-limit()-db.courses.find().limit(1).skip(2) 
 3-sort()-db.courses.find().sort({"Course":-1})  
 
 
 ///BASIC USER AUTHENTICATION///
 
use admin
db.createUser(
  {
    user: "shweta",
    pwd: "soni",
    roles: [ { role: "userAdminAnyDatabase", db: "admin" } ]
  })
  [shweta ~]$ mongo admin
MongoDB shell version: 3.0.7
connecting to: admin
>

///SIMULATING DB USING SIMPLE PROGRAM///

public class TestDBMonitor extends TestCase {

     @override
    public void setUp() throws Exception {

       MockConnection connection = new MockConnection();

       this.tableName = "table1";
       MockTable table = new MockTable(tableName);

       String columnName = "column1";
       ColumnType columnType = ColumnType.NUMBER;
       int columnSize = 50;
       MockColumn column = new MockColumn(columnName, columnType, columnSize);
       table.addColumn(column);

       for (int i = 0; i < 20; i++) {
           HashMap<MockColumn, Object> fields = new HashMap<MockColumn, Object>();
           fields.put(column, i);
           table.addRow(fields);
       }

       this.connection = connection;
    }

    @Test
    public void testGatherStatistics() throws Exception {

       DBMonitor monitor = new DBMonitor(connection);
       monitor.gatherStatistics();
       assertEquals(((MockConnection) connection).getNumberOfRows(tableName),
                    monitor.getNumberOfRows(tableName));
    }

    String tableName;
    Connection connection;
}
 
  
