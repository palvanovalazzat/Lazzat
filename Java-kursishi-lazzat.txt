//birinchi qiladigan ishimiz  mysql-connector-j-8.0.31 ni o`rnatib olishimiz kerak

import java.sql.*;

//Class yaratamiz
public class JavadagilarUchun {
    public static void main(String[] args)
    {
        try
        {
            // create our mysql database connection
            //String myDriver = "org.gjt.mm.mysql.Driver";
            String myUrl = "jdbc:mysql://localhost/akmal";
            //Class.forName(myDriver);
            Connection conn = DriverManager.getConnection(myUrl, "user", "password"); // bu yerda mysql foydalanuchi nomi va kodini kiritamiz

            // our SQL SELECT query.
            // if you only need a few columns, specify them by name instead of using "*"
             
            String query = "SELECT * FROM bazanomi.tablitsanomi";

            // create the java statement
            Statement st = conn.createStatement();

            // execute the query, and get a java resultset
            ResultSet rs = st.executeQuery(query);

            // iterate through the java resultset
            while (rs.next())
            {
                int id = rs.getInt("id");
                String nomer = rs.getString("nomer");
                String index_p = rs.getString("index_p");
                String sost = rs.getString("sost");
                String stansiya = rs.getString("stansiya");
                Date datatime = rs.getDate("datatime");

                // print the results
                System.out.format("%s, %s, %s, %s, %s, %s\n", id, nomer, index_p, sost, stansiya, datatime);
            }
            st.close();
        }
        catch (Exception e)
        {
            System.err.println("Got an exception! ");
            System.err.println(e.getMessage());
        }
    }
}